# Kubesphere NetworkPolicy

## Overview

Kubesphere mutitenancy use workspace and namespace to implement the isolation of various resources, but the network is not currently isolated, workspace and project can access each other by default.

Now kubernetes defines NetworkPolicy CRD, we can use it to achieve network isolation. Kubernetes NetworkPolicy defines three selectors, i.e., pod, namespace and cidr. Pod is the smallest scheduling unit of the system. Generally people use service to expose them. In order to  minimize the concept of pod and improve ease of use, we introduce the service selector and reuse the labels in select.

## Implement

There are two kinds of isolation i.e., workspace and project. Workspace uses a new field `"networkIsolation"` in spec, and project uses namespace annotation `"kubesphere.io/network-isolate = enabled"`. The two types of isolation are different from the design of kubernetes NetworkPolicy, they cannot coexist in a cluster, so we can just choose one of them to achieve the isolation.

* When a workspace is isolated, the following Kubernetes NetworkPolicy will be added in all namespaces in the same workspace, deny all incoming traffic except traffic in same workspace:

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
  policyTypes:
  - ingress
```

* When a project is isolated, the following Kubernetes NetworkPolicy will be added in the namespace, deny all incoming traffic except traffic in the same namespace:

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
  policyTypes:
  - ingress
```

Let's say I have two projects, A and B. They are in the same workspace. If the A and B have not been set an annotation "kubesphere.io/network-isolate = enabled", they can access each other. The same thing goes for services. If project A has been set an annotation `"kubesphere.io/network-isolate = enabled"`, A cannot access services in B, unless A allows egress for services in B.

## The Namespace NetworkPolicy resource 
See the [Namespace NetworkPolicy](https://github.com/kubesphere/kubesphere/blob/d3bdcd0/pkg/apis/network/v1alpha1/namespacenetworkpolicy_types.go#L31) reference for a full definition of the resource.
With the exception of this field `service`, the fields are the same as kubernetes NetworkPolicy.

Let's take an example of NetworkPolicy for a Namespace:
```yaml
apiVersion: network.kubesphere.io/v1alpha1
kind: NamespaceNetworkPolicy
metadata:
  name: test-nsnp
  namespace: default
spec:
  egress:
    - to:
      - service:
          name: my-svc
          namespace: my-project
```

The example policy contains a single rule, which matches the traffic selected by a service.

When a policy contains an egress rule to service is added, the following egress traffic will be allowed automatically:
* DNS traffic, only port 53 and protocol TCP/UDP

## Source IP

When we use CIDR in Namespace NetworkPolicy, we should know what happens to the source IP of packets.

Packets sent to ClusterIP/PodIP from within the cluster are never source NAT'd by default.
However, if you're setting `masqueradeAll` to true, the source IP will be changed to  node IP or overlay tunnel IP.

Packets sent to Services with `Type=LoadBalancer or NodePort` are source NAT'd by default, because all schedulable Kubernetes nodes in the Ready state are eligible for load-balanced traffic. So if packets arrive at a node without an endpoint, the system proxies it to a node with an endpoint, replacing the source IP on the packet with the IP of the node.
However, if you're setting the `service.spec.externalTrafficPolicy` field to Local, the packets will only be sent to the node which they arrived, and the source IP will not be replaced.

## Future

## References

* Using Source IP: <https://kubernetes.io/docs/tutorials/services/source-ip/>
* Network Policies: <https://kubernetes.io/docs/concepts/services-networking/network-policies/>