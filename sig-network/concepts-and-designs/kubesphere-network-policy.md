# Kubesphere Network Policy

## Overview

Kubesphere mutitenancy use workspace and namespace to implement the isolation of various resources, but the network is not currently isolated, workspace and project can access each other by default.

Now kubernetes defines NetworkPolicy CRD, we can use it to achieve network isolation. Kubernetes NetworkPolicy defines three selectors, i.e., pod, namespace and cidr. Pod is the smallest scheduling unit of the system. Generally people use service to expose them. In order to  minimize the concept of pod and improve ease of use, we introduce the service selector and reuse the labels in select.

## Implement

There two kinds of isolation i.e., workspace and project. Workspace uses a new field "networkIsolation" in spec, and project uses namespace annotation "kubesphere.io/network-isolate = enabled". The two types of isolation, which are different from the design of K8s network policy, cannot coexist, so we can just
use one of them to achieve the isolation.

* When a workspace is isolated, the following Kubernetes NetworkPolicy will be added in all namespaces in the same workspace, deny all incoming and outgoing traffic except traffic in same workspace:

```yaml
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

* When a project is isolated, the following Kubernetes NetworkPolicy will be added in the namespace, deny all incoming and outgoing traffic exception traffic in the same namespace:

```yaml
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

* DNS traffic, only port 53 and protocol TCP/UDP
* All nodes internal IP, such as IP on eth0

Let's say I have two projects, A and B. They are in same workspace. If the A and B have not set annotation "kubesphere.io/network-isolate = enabled", they can access each other. The same thing goes for services. If project A set annotation "kubesphere.io/network-isolate = enabled", A cannot access services in B, unless A allows egress for services in B.

## Future

Now it just works correctly when proxy mode is iptables, because ipvs will use src ip that is assigned by CNI plugin. But we cannot obtain this ip. we will support ipvs in future.

## References

* Using Source IP: <https://kubernetes.io/docs/tutorials/services/source-ip/>
* Network Policies: <https://kubernetes.io/docs/concepts/services-networking/network-policies/>