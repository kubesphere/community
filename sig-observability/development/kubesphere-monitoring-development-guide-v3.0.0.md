# KubeSphere Monitoring

This documentation contains backend development guide for interaction with key components behind KubeSphere monitoring system. KubeSphere monitoring system provides the functionality of metric searching, ranking and custom monitoring.

## File Tree

The listing below covers relevant code for monitoring.

```yaml
/cmd
  └─ks-apiserver
      └─app
          └─options         # initialize monitoring client when launching ks-apiserver
              ├─options.go
              └─validation.go
/pkg
  ├─kapis                   # register monitoring apis
  │  └─monitoring
  │      └─v1alpha3
  │          ├─handler.go
  │          ├─helper.go   # utilities for parsing and validating request parameters
  │          └─register.go # register monitoring apis
  ├─models
  │  └─monitoring
  │      ├─monitoring.go    # interact with the monitoring client
  │      ├─named_metrics.go # KubeSphere internally supported metrics (used in the request parameter `metric_filter`)
  │      ├─sort_page.go     # rank metrics
  │      ├─types.go         # define monitoring api response structure
  │      └─expressions      # namespace label value modifier for querying user-defined metrics in a multi-tenant environment
  │          ├─prometheus.go # a prometheus implementation of namespace modifier
  │          └─registery.go  # modifier registry
  └─simple
     └─client
        └─monitoring
           ├─interface.go              # define monitoring client interfaces
           ├─query_options.go          # define query option types
           ├─types.go                  # define return value structures
           └─prometheus                # a prometheus implementation of monitoring client
               ├─prometheus.go         # prometheus client code
               ├─prometheus_options.go # prometheus client options
               └─promql.go             # construct promql expressions for named metrics
```

## API Design

### Querying Named Metrics

Named metrics are KubeSphere internally supported metrics for common resources of 10 levels (see [named_metrics.go](https://github.com/kubesphere/kubesphere/blob/v3.0.0/pkg/models/monitoring/named_metrics.go)).

```
# Get platform-level metrics
GET /kubesphere

# Get cluster-level metrics
GET /cluster

# Get node-level metrics
GET /nodes
GET /nodes/{node}

# Get workspace-level metrics
GET /workspaces
GET /workspaces/{workspace}

# Get namespace-level metrics
GET /workspaces/{workspace}/namespaces
GET /namespaces
GET /namespaces/{namespace}

# Get workload-level metrics
GET /namespaces/{namespace}/workloads
GET /namespaces/{namespace}/workloads/{kind}

# Get pod-level metrics
GET /namespaces/{namespace}/pods
GET /namespaces/{namespace}/pods/{pod}
GET /namespaces/{namespace}/workloads/{kind}/{workload}/pods
GET /nodes/{node}/pods
GET /nodes/{node}/pods/{pod}

# Get container-level metrics
GET /namespaces/{namespace}/pods/{pod}/containers
GET /namespaces/{namespace}/pods/{pod}/containers/{container}

# Get pvc-level metrics
GET /storageclasses/{storageclass}/persistentvolumeclaims
GET /namespaces/{namespace}/persistentvolumeclaims
GET /namespaces/{namespace}/persistentvolumeclaims/{pvc}

# Get component-level metrics (etcd, kube-apiserver, kube-scheduler)
GET /components/{component}
```

### Custom Monitoring

Custom monitoring allows users to make user-defined metric queries beyond the scope of named metrics.

```
# List available metrics and their metadada
GET  /namespaces/{namespace}/targets/metadata

# Fetch all metric label value pairs
GET  /namespaces/{namespace}/targets/labelsets?metric=<metric>

# Ad-hoc metric query
GET  /namespaces/{namespace}/targets/query?expr=<expression>
```