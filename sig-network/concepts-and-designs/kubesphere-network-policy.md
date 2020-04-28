# Kubesphere NetworkPolicy

## Overview
Kubesphere mutitenancy use workspace and namespace to implement the
isolation of various resources, but the network is not currently isolated,
workspace and project can access each other default.

Now kubernetes defines NetworkPolicy CRD, we can use it to achieve network
isolation. Kubernetes NetworkPolicy define three selector, pod, namespace, cidr. 
Pod is the smallest scheduling unit of the system, generally people use service
expose them. In order to  minimize the concept of pod, improve ease of use, we 
introduce the service selector, reuse the labels in select.


## Implement
There two kind isolation, workspace and project. workspace use a new field
"networkIsolation" in spec, and project use namespace annotation 
"kubesphere.io/network-isolate = enabled". I think those two isolation,
just different in k8s network policy, they cannot coexist, so we can just
use one k8s network policy do this.

When a workspace is isolated, the following Kubernetes NetworkPolicy will
be added in all namespaces in same workspace, deny all incoming and outgoing traffic
except traffic in same workspace:
```
apiVersion: "networking.k8s.io/v1"
kind: "NetworkPolicy"
metadata:
  name: network-isolate
  namespace: ${namespace-name}
spec:
  podSelector: {}
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              "kubesphere.io/workspace": ${workspace-name}
  Egress:
    - To:
        - namespaceSelector:
            matchLabels:
              "kubesphere.io/workspace": ${workspace-name}
```
              
When a project is isolated, the following Kubernetes NetworkPolicy will be
added in namespace, deny all incoming and outgoing traffic exception traffic
in same namespace:
```
apiVersion: "networking.k8s.io/v1"
kind: "NetworkPolicy"
metadata:
  name: network-isolate
  namespace: ${namespace-name}
spec:
  podSelector: {}
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              "kubesphere.io/namespace": ${namespace-name}
  Egress:
    - To:
        - namespaceSelector:
            matchLabels:
              "kubesphere.io/workspace": ${namespace-name}
```
              
Beyond that, we also allow the bellowing traffic:
* Dns traffic, only port 53 and protocol TCP/UDP
* All nodes internal IP, such as IP on eth0

Let's say I have two projects, A and B, they are in same workspace. If 
the A and B have not set annotation "kubesphere.io/network-isolate = enabled",
they can access each other, the same goes for services. If project A set 
annotation "kubesphere.io/network-isolate = enabled", A cannot access service 
 in B, unless A allow egress for service in B.

##Future
Now it just work correctly when proxy mode is iptables, because ipvs will use src ip 
which assigned by cni plugin, and we cannot obtain this ip. we will support ipvs in 
future.

##References
Using Source IP: https://kubernetes.io/docs/tutorials/services/source-ip/

Network Policies: https://kubernetes.io/docs/concepts/services-networking/network-policies/