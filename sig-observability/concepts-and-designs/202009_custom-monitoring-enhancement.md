Custom Monitoring Enhancement

# Summary

This proposal describes custom monitoring enhancements as of KubeSphere 3.0.0. The aim is to further improve the user experience. The bundle of enhancements is listed below:

- Configure ServiceMonitor via UI
- PromQL auto-completion and syntax highlighting
- Import dashboards from Grafana templates
- Support query variables
- Support cluster-level custom monitoring
- Support federated dashboard CRD

# E1. Configure ServiceMonitor via UI

To integrate custom application metrics into the KubeSphere monitoring engine, users need to install a ServiceMonitor object. In KubeSphere 3.0.0, for project users, the only way to do so is deploying the application helm chart with the ServiceMonitor YAML file included. We realized it is extremely sophisticated for users. To relieve the pain, we propose the feature of configuring ServiceMonitor via UI. The following table is derived and adapted from [Prometheus Operator API docs](https://github.com/prometheus-operator/prometheus-operator/blob/master/Documentation/api.md). We only keep fields used in KubeSphere UI.

## ServiceMonitor

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| metadata |  | [metav1.ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#objectmeta-v1-meta) | false |
| spec | Specification of desired Service selection for target discovery by Prometheus. | [ServiceMonitorSpec](#servicemonitorspec) | true |

## ServiceMonitorSpec

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| endpoints | A list of endpoints allowed as part of this ServiceMonitor. | [][Endpoint](#endpoint) | true |
| selector | Selector to select Endpoints objects. | [metav1.LabelSelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#labelselector-v1-meta) | true |

## Endpoint

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| port | Name of the service port this endpoint refers to. Mutually exclusive with targetPort. | string | false |
| path | HTTP path to scrape for metrics. Defaults to `/metrics`.| string | false |
| scheme | HTTP scheme to use for scraping. Defaults to `http`.| string | false |
| params | Optional HTTP URL parameters | map[string][]string | false |
| interval | Interval at which metrics should be scraped. Defaults to `1m`.| string | false |
| scrapeTimeout | Timeout after which the scrape is ended | string | false |
| tlsConfig | TLS configuration to use when scraping the endpoint | *[TLSConfig](#tlsconfig) | false |
| bearerTokenSecret | Secret to mount to read bearer token for scraping targets. The secret needs to be in the same namespace as the service monitor and accessible by the Prometheus Operator. | [v1.SecretKeySelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#secretkeyselector-v1-core) | false |
| basicAuth | BasicAuth allow an endpoint to authenticate over basic authentication More info: https://prometheus.io/docs/operating/configuration/#endpoints | *[BasicAuth](#basicauth) | false |

## TLSConfig

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| ca | Struct containing the CA cert to use for the targets. | SecretOrConfigMap | false |
| cert | Struct containing the client cert file for the targets. | SecretOrConfigMap | false |
| keySecret | Secret containing the client key file for the targets. | *[v1.SecretKeySelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#secretkeyselector-v1-core) | false |
| serverName | Used to verify the hostname for the targets. | string | false |
| insecureSkipVerify | Disable target certificate validation. | bool | false |

## SecretOrConfigMap

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| secret | Secret containing data to use for the targets. | *[v1.SecretKeySelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#secretkeyselector-v1-core) | false |

## BasicAuth

| Field | Description | Scheme | Required |
| ----- | ----------- | ------ | -------- |
| username | The secret in the service monitor namespace that contains the username for authentication. | [v1.SecretKeySelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#secretkeyselector-v1-core) | false |
| password | The secret in the service monitor namespace that contains the password for authentication. | [v1.SecretKeySelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.17/#secretkeyselector-v1-core) | false |

The workflow of this enhancement is: (1) the user first clicks the target application (or exporter) service and chooses this service as the monitoring target; (2) Within the pop-up, the user inputs all necessary information (see the table above) about the monitoring target; (3) the frontend makes use of the preceding parameters to construct a ServiceMonitor object and posts a create request to Kubernetes cluster; (4) the ServiceMonitor object is created. The task is completed.

# E2. PromQL Autocompletion and Syntax Highlighting

We compare two ways to implement auto-completion functionality: application-specific implementation and language-server based implementation. Considering the Prometheus community is still working hard on the [language server protocol for PromQL](https://github.com/prometheus-community/promql-langserver), we suggest starting with the former.

## Application-specific implementation

In the application-specific implementation, PromQL parsing is performed by the application itself. For projects like Prometheus, Grafana, and Thanos, they implement autocompletion functionality in this way. Different applications have different implementations that cause duplicate efforts. Besides, some only implement a limited set of auto-completion feature. See the [blog](https://kausal.co/blog/prometheus-tab-completion-open-source/) for Grafana implementation.  

## Language-server based implementation

To solve the problem above, setting up a PromQL language server is a promising and unified way to implement the feature set of autocompletion, syntax highlighting, and syntax check. Please refer to the project [promql-langserver](https://github.com/prometheus-community/promql-langserver) for more information.

The API to return label-value pairs per metric is `/namespaces/{namespace}/targets/labelsets?metric=<metric>`. An example of the response:

```
GET /kapis/monitoring.kubesphere.io/v1alpha3/namespaces/kubesphere-monitoring-system/targets/labelsets?metric=kube_configmap_info&start=1589490211&end=1589500211
---
{
    "data":[
        {
            "configmap":"grafana-dashboard-cluster-total",
            "endpoint":"https-main",
            "instance":"10.233.99.140:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-prwbc",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-cluster-total",
            "endpoint":"https-main",
            "instance":"10.233.99.172:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-6x2gr",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-cluster-total",
            "endpoint":"https-main",
            "instance":"10.233.99.173:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-6646f8489d-2l482",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-cluster-total",
            "instance":"10.233.99.140:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-prwbc"
        },
        {
            "configmap":"grafana-dashboard-k8s-resources-workload",
            "endpoint":"https-main",
            "instance":"10.233.99.173:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-6646f8489d-2l482",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-k8s-resources-workload",
            "instance":"10.233.99.140:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-prwbc"
        },
        {
            "configmap":"grafana-dashboard-k8s-resources-workload",
            "instance":"10.233.99.172:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-6x2gr"
        },
        {
            "configmap":"grafana-dashboard-namespace-by-pod",
            "instance":"10.233.99.172:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-6x2gr"
        },
        {
            "configmap":"grafana-dashboard-persistentvolumesusage",
            "endpoint":"https-main",
            "instance":"10.233.99.140:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-prwbc",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-persistentvolumesusage",
            "endpoint":"https-main",
            "instance":"10.233.99.172:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-6x2gr",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-persistentvolumesusage",
            "endpoint":"https-main",
            "instance":"10.233.99.173:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-6646f8489d-2l482",
            "service":"kube-state-metrics"
        },
        {
            "configmap":"grafana-dashboard-proxy",
            "instance":"10.233.99.172:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-6x2gr"
        },
        {
            "configmap":"grafana-dashboard-scheduler",
            "endpoint":"https-main",
            "instance":"10.233.99.140:8443",
            "job":"kube-state-metrics",
            "namespace":"kubesphere-monitoring-system",
            "pod":"kube-state-metrics-869dc86c5b-prwbc",
            "service":"kube-state-metrics"
        }
    ]
}
```

# E3. Import Dashboards from Grafana Templates

The data model for [KubeSphere monitoring dashboard](https://github.com/kubesphere/monitoring-dashboard) is heavily inspired by Grafana, the open-source observability tool. Considering the wide use of Grafana, we suggest allowing KubeSphere users to import dashboards from existing Grafana templates.

# E4. Support Query Variables

For users familiar with Grafana, query variable is a helpful feature when it comes to write PromQL expressions, KubeSphere monitoring dashboard supports Grafana-like query templating to keep capability with Grafana dashboards. As planned, we will first support the following functions to fetch candidate values:

|Function|Description|
|---|---|
|label_values(\<label\>)|List all label values from every metric|
|label_value(\<metric\>, \<label\>)|List all label values from the specific metic|

To use variables in dashboards, you put `$<variable_name>` in place in your PromQL expressions.

# E5. Support Cluster-Level Custom Monitoring

In KubeSphere 3.0.0, custom monitoring is a namespace-scoped feature. Users can only create custom monitoring dashboards per project for namespace-scoped resources. However, there are many cluster-scoped resources, for example, GPU cores. In future releases, we will support cluster-level custom monitoring.  

# E6. Support Federated Dashboard CRD

Monitoring dashboard configuration is nothing short of a Kubernetes CRD object. To support the multi-cluster management feature, we will support the federated dashboard CRD.