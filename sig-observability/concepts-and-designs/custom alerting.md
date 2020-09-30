# Custom Alerting

The current solution is based on prometheus and thanos, and mainly provides the following functions:

- Multi-tenancy of prometheus alerts and rules
- Display and update of prometheus rules
- Display of prometheus alerts
- Silence rule of prometheus alerts including display, update, multi-tenancy (based on alertmanager, and low priority according to schedule)

## [Alert Rule](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/#alerting-rules)

Here for a single cluster, the backend of thanos query should be configured with prometheus's thanos sidecar and thanos ruler.
> - From the perspective of the alert function, thanos sidecar is a proxy of Prometheus, and ruler is a prometheus that removes the metric scrape function.  
> - Thanos ruler is optional, it is used here to avoid prometheus service restart that may be caused when the rules are added or updated. (It is also needed to provide global alerts for multi-cluster)

### Rule Source

- svc: `thanos-query.kubesphere-monitoring-system.svc`
- endpoint: [/api/v1/rules](https://github.com/prometheus/alertmanager/blob/master/api/v2/openapi.yaml#L130)
- resp body format: 
    ```json
    {
        "status": "success",
        "data": {
            "groups": [
                {
                    "name": "kubernetes-resources",
                    "file": "/etc/prometheus/rules/prometheus-k8s-rulefiles-0/kubesphere-monitoring-system-prometheus-k8s-rules.yaml",
                    "rules": [
                        {
                            "state": "firing",
                            "name": "KubeCPUOvercommit",
                            "query": "sum(namespace:kube_pod_container_resource_requests_cpu_cores:sum) / sum(kube_node_status_allocatable_cpu_cores) > (count(kube_node_status_allocatable_cpu_cores) - 1) / count(kube_node_status_allocatable_cpu_cores)",
                            "duration": 300,
                            "labels": {
                                "severity": "warning"
                            },
                            "annotations": {
                                "message": "Cluster has overcommitted CPU resource requests for Pods and cannot tolerate node failure.",
                                "runbook_url": "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubecpuovercommit"
                            },
                            "alerts": [
                                {
                                    "labels": {
                                        "alertname": "KubeCPUOvercommit",
                                        "severity": "warning"
                                    },
                                    "annotations": {
                                        "message": "Cluster has overcommitted CPU resource requests for Pods and cannot tolerate node failure.",
                                        "runbook_url": "https://github.com/ kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubecpuovercommit"
                                    },
                                    "state": "firing",
                                    "activeAt": "2020-09-22T06:18:47.55260138Z",
                                    "value": "4.405e-01"
                                }
                            ],
                            "health": "ok",
                            "evaluationTime": 0.000894038,
                            "lastEvaluation": "2020-09-22T08:57:17.566233983Z",
                            "type": "alerting"
                        }
                    ]
                }
            ]
        }
    }
    ```

### Rule Show

ui field | corresponding field | illustration | remarks
 --- | --- | --- | ---
name | `rules[].name` | alert rule name (same to alert name) | 规则名称
query | `rules[].query` | [promql](https://prometheus.io/docs/prometheus/latest/querying/basics/). Use it to query metric and show metric graph on secondary page | 表达式/查询语句
duration | `rules[].duration` | duration to presist for alert from `pending` to `firing` state | 持续时间
severity | `rules[].labels.severity` | mark severity of the alert (`info`,`warning`,`critical`) | 级别
health | `rules[].health` | [health state](https://github.com/prometheus/prometheus/blob/master/rules/manager.go#L45) of a rule (`unknown`, `ok`, `err`) | 健康状态
state | `rules[].state` | [rule state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L431): maximum state of alert instances for this rule (`firing` > `pending` > `inactive`) | 触发状态
/ | / | / | /
/ | `rules[].alerts` | alerts triggered by current rule. Show them on secondary page | 告警
name | `rules[].alerts[].name` | alert name (same to rule name) | 告警名称
message | `rules[].alerts[].message` | usually used to record the details of an alert, and it may be not exist | 告警消息
state | `rules[].alerts[].state` | [alert state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L57) (`inactive`, `pending`, `firing`) | 告警状态

> - [The alerting ui of openshift](https://docs.openshift.com/container-platform/4.5/monitoring/cluster_monitoring/managing-cluster-alerts.html) can be referred to.
> - Multi-tenant control: Isolate according to the crd instance of [prometheus rule](https://github.com/prometheus-operator/prometheus-operator/blob/master/Documentation/api.md#prometheusrule)
> - rules grouping: [each group will be arranged a goroutine](https://github.com/prometheus/prometheus/blob/master/rules/manager.go#L953)
> - rules list is based on the rules in the crd instances, and the status information of the rules is obtained from `/rules` api


### Rule Add & Edit

#### Positioning Rules

The rules obtained from ThanosQuery/Prometheus have a `groups[].file` field which has following format:  
`${rules_dir}/${cm_name}/${prometheusrule_ns}-${prometheusrule_name}.yaml`  
Then it can be uniquely determined by the following attributes:

- `groups[].name`
- `groups[].file`
- `rules[].name`
- `rules[].duration`
- `rules[].query`
- `rules[].labels`

Generate id through these attributes, and then when modifying the rule, locate the old rule according to the id to facilitate accurate modification.
> When adding a rule, it is also necessary to check whether the corresponding rule already exists.  
> crd instance size check

#### Rule Edit UI

| ui field | illustration | remarks
| --- | --- | ---
| name | required | 规则名称
| query | required | 表达式
| duration | - | 持续时间
| labels | addable | 标签(触发告警时将被添加至alert的labels)，例如`severity`
| annotations | addable | 注释(触发告警时将被添加至alert的annotations)，可[模板化](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/#templating)，例如`summary`, `message`, `runbook_url`, `description`

#### Query Edit UI

- Graphical configuration of some simple basic expressions： 

    | ui field | illustration | remarks
    | --- | --- | ---
    | metric_name | cpu usage, memory usage, etc.
    | workloads | including kind and name
    | comparator | >, >=, <, <= | 比较符
    | threshold | | 阈值
    
    > query: `namespace:workload_memory_usage:sum{namespace="${namespace}",owner_kind="${kind}",workload="${kind}:${workload_name}"} ${comparator} ${threshold}`  
    eg: `namespace:workload_memory_usage:sum{namespace="test",owner_kind="Deployment",workload="Deployment:details-v1"} > 10485760`

- Syntax tips in non-graphical configuration  
    > refer to grammar tips on grafana's ui

## Alert

### Alert Source

It is same to [alert rule source](#rule-source), but the alerts part is mainly used.  
> - The alerts here do not include all historical alerts

### Alert Show 

ui field | corresponding field | illustration | remarks
--- | --- | --- | ---
name | `rules[].alerts[].name` |  | 告警名称
severity | `rules[].alerts[].labels.severity` | mark severity of the alert (`info`,`warning`,`critical`) (It may be not exist) | 级别
message | `rules[].alerts[].labels.message` | It may be `description` or not exist  | 消息
summary | `rules[].alerts[].labels.summary` | It may be not exist  | 摘要
state | `rules[].alerts[].state` | [alert state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L57) (`inactive`, `pending`, `firing`) | 状态

> - For project users, the alerts under the rules belonging to the current tenant and the alerts related to the current tenant under the system rules should be displayed.  
> - Show the corresponding rule on secondary page.
> - Inactive alerts may not be displayed because they are usually resolved but kept in memory state for a certain period of time and sent to the alertmanager.

### Alert Silence