# Custom Alerting

The current solution is based on prometheus and thanos, and mainly provides the following functions:

- Multi-tenancy of prometheus alerts and rules
- CRUD of alerting rules
- Query of alerts
- Silence of alerts including multi-tenancy and CRUD for silence rules
    > silence rule design is based on alertmanager, and has lower priority

Components that may be dependent are as follows:
- **Prometheus**: It means prometheus server. In this solution, It plays a role of providing metric query api and evaluating built-in alerting rules to generate alerts, , and provides rules and alerts query, too.
- **Thanos Ruler**: It evaluates custom alerting rules against metric query API to generate alerts, and provides rules and alerts query, too.
- **Thanos Query**: Here, some of its functions, such as rules and alerts query, will be used. It is especially necessary in multi-cluster mode.
- **Prometheus-operator**: By it, addition, modification, deletion to the rules will be instantly loaded to Prometheus and Thanos Ruler, and multi-tenancy of alerting rules and alerts can be achieved. The CRDs as follows may be used:
    - **PrometheusRule**: It holds a list of alerting rules.
    - **Prometheus**: It defines a prometheus component which will load alerting rules in its selected PrometheusRule instances.
    - **ThanosRuler**: It defines a thanos ruler component which will load alerting rules in its selected PrometheusRule instances. 

## [Alerting Rule](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/#alerting-rules)

Multi-tenant processing of alerting rules has to be rely on PrometheusRule instances. The rules and alerts apis should be called to get state of rules and their alerts. Coordinate the processing of the two to better realize the operation of the rules

### Rule Source

Services that may be used are as follows:
- prometheus: `prometheus-operated.kubesphere-monitoring-system.svc`
- thanos ruler: `thanos-ruler-operated.kubesphere-monitoring-system.svc`
- thanos query: `thanos-query.kubesphere-monitoring-system.svc`

They have a common api called `/api/v1/rules`, but the difference in response body , that may be caused by the different versions of Prometheus they rely on, should require attention. The following is a response from thanos query: 
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

### Rule Dispaly

field | data field | desc | remarks
 --- | --- | --- | ---
name | `rules[].name` | alerting rule name | 规则名称
query | `rules[].query` | [promql](https://prometheus.io/docs/prometheus/latest/querying/basics/). It can be used to query metric and show metric graph on secondary page | 表达式/查询语句
duration | `rules[].duration` | duration to persist for alert from `pending` to `firing` state | 持续时间
severity | `rules[].labels.severity` | a typical label which marks severity of the alert (`info`,`warning`,`critical`) | 级别
health | `rules[].health` | [health state](https://github.com/prometheus/prometheus/blob/master/rules/manager.go#L45) of a rule (`unknown`, `ok`, `err`) | 健康状态
state | `rules[].state` | [rule state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L431): maximum state of alert instances for this rule (`firing` > `pending` > `inactive`) | 触发状态
/ | / | / | /
/ | `rules[].alerts` | alerts triggered by current rule. Show them on secondary page | 告警
name | `alerts[].labels.alertname` | alert name (same to rule name) | 告警名称
message | `alerts[].labels.message` | usually used to record the details of an alert, and may be not exist | 告警消息
state | `alerts[].state` | [alert state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L57) (`inactive`, `pending`, `firing`) | 告警状态
value | `alerts[].value` | the result of rule query expression evaluation | 告警值
activeAt | `alerts[].activeAt` | time when alert is active | 激活时间

> - Multi-tenant control: Isolate according to the crd instances of [prometheus rule](https://github.com/prometheus-operator/prometheus-operator/blob/master/Documentation/api.md#prometheusrule)
> - rules list is based on the rules in the prometheusrule crd instances. The status information and related alerts of the rules is obtained from `/rules` api


### Rule Management

#### Positioning Rules

The rules obtained from Prometheus/ThanosRuler/ThanosQuery have a `groups[].file` field which has following format:  
`${rules_dir}/${cm_name}/${prometheusrule_ns}-${prometheusrule_name}.yaml`.  
Then it can be uniquely determined by the following attributes:

- `groups[].name`
- `groups[].file`
- `rules[].name`
- `rules[].duration`
- `rules[].query`
- `rules[].labels`

Generate id through these attributes, and then when modifying the rule, locate the old rule according to the id to facilitate accurate modification.
> It is also necessary to check whether the corresponding rule already exists when adding a rule.
> Crd instance size check to avoid exceeding the size limit when adding a rule.

#### Rule Edit UI

It should provide the following fields to add or edit alerting rules.

| field | desc | remarks
| --- | --- | ---
| name | required | 规则名称
| query | required | 表达式
| duration | - | 持续时间
| labels | addable | 标签(触发告警时将被添加至alert的labels)，例如`severity`
| annotations | addable | 注释(触发告警时将被添加至alert的annotations)，可[模板化](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/#templating)，例如`summary`, `message`, `runbook_url`, `description`

#### Query Edit UI

The query field is a prometheus query expression which has its self [grammars](https://prometheus.io/docs/prometheus/latest/querying/basics/).  
- For some common basic metrics, graphical configuration may be convenient. For example, the following attributes can be provided to construct a simple expression.

    | field | desc | remarks
    | --- | --- | ---
    | metric_name | cpu usage, memory usage, etc.
    | workload_kind | workload kind
    | workload_name | workload name
    | comparator | >, >=, <, <= | 比较符
    | threshold | | 阈值
        
    > template: `namespace:workload_memory_usage:sum{owner_kind="${workload_kind}",workload="${workload_kind}:${workload_name}"} ${comparator} ${threshold}`  
        expression: `namespace:workload_memory_usage:sum{owner_kind="Deployment",workload="Deployment:details-v1"} > 10485760`

- Complex expressions have to be edited manually with non-graphical configuration
    > refer to grammar tips on grafana's ui

## Alert

### Alert Source
Same to [alert rule source](#rule-source), alerts can be obtained by the same api. Multi-tenancy and association between alerts and rules should be handled too.
> - The alerts here do not include all historical alerts

### Alert Display 

field | data field | desc | remarks
--- | --- | --- | ---
name | `alerts[].labels.alertname` | alert name | 告警名称
severity | `alerts[].labels.severity` | mark severity of the alert (`info`,`warning`,`critical`) (It may be not exist) | 级别
message | `alerts[].labels.message` | may be `description` or not exist  | 消息
summary | `alerts[].labels.summary` | may not exist  | 摘要
state | `alerts[].state` | [alert state](https://github.com/prometheus/prometheus/blob/master/rules/alerting.go#L57) (`inactive`, `pending`, `firing`) | 状态
value | `alerts[].value` | the result of rule query expression evaluation | 告警值
activeAt | `alerts[].activeAt` | time when alert is active | 激活时间

> - For project users, the alerts under the rules belonging to the current tenant and the alerts related to the current tenant under the system rules should be displayed.  
> - The corresponding rule to alert can be displayed on secondary page.
> - Inactive alerts may not be displayed because they are usually resolved but kept in memory state for a certain period of time and sent to the alertmanager.

### Alert Silence

TODO

## API Design

The apis as follows may be provided. They are divided into two levels: cluster level and namespace level.

- list rules
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/rules
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules  
    - filters：
        - rulename
        - state
        - health
    - sort
- get a certain rule
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/rules/{ruleId}
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules/{ruleId}
- add a rule
    - Post /kapis/custom.alerting.kubesphere.io/v1alpha1/rules
    - Post /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules
- update a certain rule
    - Post /kapis/custom.alerting.kubesphere.io/v1alpha1/rules/{ruleId}
    - Post /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules/{ruleId}
- delete a certain rule
    - Delete /kapis/custom.alerting.kubesphere.io/v1alpha1/rules/{ruleId}
    - Delete /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules/{ruleId}
- list alerts
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/alerts
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/alerts  
    - filters：
        - alertname 
        - state
    - sort
- list alerts of a certain rule
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/rules/{ruleId}/alerts
    - Get /kapis/custom.alerting.kubesphere.io/v1alpha1/namespaces/{namespace}/rules/{ruleId}/alerts