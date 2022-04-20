# KubeSphere Gateway Operator design

## Objective

The KubeSphere Gateway is an Ingress Controller that serves Ingress resources to provide external access ability to cluster internal services.

Gateway(Router) API used to be designed as declarative API to create/modify/delete the KubeSphere Gateway with Deployment and Service. And this approach was different from the Ingress Nginx Controller official Helm chart. So the legacy design was not flexible enough to add extra configurations, such as increasing replicas, upgrading the controller, etc.

As Operator becomes a common pattern to make use of custom resources to manage applications and their components. We decide to refactor the Gateway component with the Helm Operator. 

## Outline

- Current gateway features are all kept, including change gateway type( NodePort or LoadBalancer), enabling application governing, add extra annotations.
- enable the Gateway for Cluster scope
- enable the Gateway for Project scope
- increase/decrease Gateway replicas
- place Gateway workloads in its watching namespace
- check Gateway logs
- metrics of the Gateway, including request total volume/ success rate/latency scrape config
- nginx configuration, limited support

## CRD of the Gateway

To adapter different Ingress Controller, we abstracted a common Kind `Gateway` for the controller. The `Gateway` kind contains common properties that are needed to setup a new Ingress Controller. KubeSphere API and UI are only interactive with the Gateway Kind. 

```YAML
# Gateway sample
apiVersion: gateway.kubesphere.io/v1alpha1
kind: Gateway
metadata:
  name: kubesphere-router-proj1
  namespace: kubesphere-controls-system # all Gateway workload will be created in the kubesphere-controls-system namespace by default. However, it's configurable in kubesphere-config when calling KubeSphere API. 
spec:
  controller:
  # controlpanel replicas. For ingress Controler that has controlpanel and workers. *Reserved field. Changing on UI isn't supported yet. 
  replicas: 1
  # annotations of the controlpanel deployment. *Reserved field. Changing on UI isn't supported yet. 
  annotations: {}
  
  # Watching scope,
  # enabled =true, watching for the project only. The user needs to specify the watching namespace.
  # enabled =false, Global gateway, watching for all namespaces.
  scope:
    enabled: false
    namespace: ""  # defaults to .Release.Namespace

  # gateway configurations. only key-value pair supported currently.
  config:
    max-bucket: 1m

  # worker workload deployment configuration
  deployment:
    annotations: 
    "servicemesh.kubesphere.io/enabled": "false"
    replicas: 1

  # 
  service:
    # Cloud LoadBalancer configurations for service
    annotations: 
      "service.beta.kubernetes.io/qingcloud-load-balancer-eip-ids": "test-ip-id"
    # Service Type, only LoadBalancer and NodePort are supported
    type: LoadBalancer

```

## The KubeSphere implementation for Nginx Ingress Controller

KubeSphere uses the Nginx Ingress Controller as the default Gateway implementation. To simplify the deployment steps, We integrated [helm-operator-plugins](https://github.com/operator-framework/helm-operator-plugins) as our Helm Operator. The Helm operator is watching for 2 CRD `Gateway` and `Nginx`.

When an `Nginx` Custom Resource (CR) is created, a new Nginx-Ingress-controller will be deployed according to the Helm chart values in the Nginx spec by the Helm operator. The Helm chart comes from the official release of the [ingress-nginx](https://github.com/kubernetes/ingress-nginx). Available values can be found [here](https://github.com/kubernetes/ingress-nginx/blob/main/charts/ingress-nginx/values.yaml). 

And we created an adapter by Helm chart that use to convert the `Gateway` CR to `Nginx` CR. In this way, we can easily change any ingress controller configurations without code changes, but in the Helm chart template. We can also adapter other Ingress controllers in the same way.

### Watch the Nginx and Gateway CR

By default, the operator watches Nginx and Gateway resource events as shown in `watches.yaml` and executes Helm releases using the specified chart:

```yaml
- group: gateway.kubesphere.io
  version: v1alpha1
  kind: Nginx
  chart: /var/helm-charts/ingress-nginx
- group: gateway.kubesphere.io
  version: v1alpha1
  kind: Gateway
  chart: /var/helm-charts/gateway
```

You can disable the Helm Operator by removing the `watchesPath` in the `kubesphere-config`, or override the watch.yaml file with your config file path:

```yaml
gateway:
  watchesPath: config/watches.yaml
```


## API definition

### Gateway APIs

KubeSphere API server exposes the following APIs to create or modify Gateways.

| URL  | Method | Descreption |
| -------- | -------- | -------- |
| /kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/     | POST     | Create Gateway that watching for the namespace.     |
| /kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/     | GET     | Get gateways(include legacy gateway and global gateway)     |
| /kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/     | PUT     | Update Gateway that watching for the namespace.      |
/kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/kubesphere-router-{ns}/upgrade | POST | Upgrade Legecy Gateway |
| /kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/     | DELETE     | Delete Gateway that watching for the namespace.     |
| /kapis/gateway.kubesphere.io/v1alpha1/gateways/     | GET     | List gateways for all namespaces.     |
| /apis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/{gateway}     | POST、PUT、DELETE     | Create\Update\Delete Gateway using the native K8S APIs.     |


### Metric API
https://github.com/kubesphere/kubesphere/pull/4227

**Currently only the following metrics are supported**

- ingress_request_count",
- ingress_request_5xx_count
- ingress_request_4xx_count
- ingress_active_connections
- ingress_success_rate
- ingress_request_duration_average
- ingress_request_duration_50percentage
- ingress_request_duration_95percentage
- ingress_request_duration_99percentage
- ingress_request_volume
- ingress_request_volume_by_ingress
- ingress_request_network_sent
- ingress_request_network_received
- ingress_request_memory_bytes
- ingress_request_cpu_usage


### Query Pod logs
| URL  | Method | Descreption |
| -------- | -------- | -------- |
|/kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/{gateway}/pods     | Get     | Get Pod workloads    |
| 
|/kapis/gateway.kubesphere.io/v1alpha1/namespaces/{namespace}/gateways/{gateway}/pods/{pod}/log     | Get     | Get Pod log    |
| 
|/kapis/gateway.kubesphere.io/v1alpha1//namespaces/{namespace}/gateways/{gateway}/log     | Get     | query pod logs, only available when Logging enabled.   |
| 

## Upgrading from an old Gateway

We can hardly perform a rolling upgrade without service interruption when upgrading from the old Gateway to the Gateway Operator. The Deployment in the Nginx Ingress Contoller's Helm chart is different from the old YAML definition(some immutable fields were changed). We had to delete the old Deployment while upgrading.
Users can decide whether/when to upgrade the old Gateway. Once they decide to upgrade to the new design, they can click the upgrade button on the UI or call the Upgrade API.

## commits

- [feat: integrate a helm sdk that use to install Gateway helm chart #4178](https://github.com/kubesphere/kubesphere/pull/4178)
- [feat: add gateway api #4193](https://github.com/kubesphere/kubesphere/pull/4193)
- [feat: ingress metrics query apis #4227](https://github.com/kubesphere/kubesphere/pull/4227)
- [feat: upgrade gateway with all legacy settings](https://github.com/kubesphere/kubesphere/pull/4230) 
- [feat: Search gateway logs with ES #4286](https://github.com/kubesphere/kubesphere/pull/4286)
- [refactor : Refactor the gateway in cluster and project kubesphere/console#2262](https://github.com/kubesphere/console/pull/2262)