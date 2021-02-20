## Project  Goal

Provide a simple mode of [PorterLB](https://porterlb.io/), which allows users to use the IP address of a Kubernetes cluster node and a service port to expose a LoadBalancer service.

## Skills to Learn/Improve

* Golang
* Kubernetes
* Linux network (iptables and IPVS)

## Details

### Background

Currently, PorterLB supports the Layer 2 mode and BGP mode for exposing LoadBalancer services in a Kubernetes cluster. Both the Layer 2 mode and BGP mode require addition configurations (Eip, BgpConf, and BgpPeer), and the BGP mode requires that the router support BGP.

We hope to provide a simple mode of PorterLB so that users can expose LoadBalancer services more easily.

### Project details

The new mode needs to support the following features:

* A LoadBalancer service can be accessed directly through the IP address of a Kubernetes cluster node and the service port without using NodePort.
* PorterLB automatically selects a Kubernetes cluster node whose port corresponding to the service port is not occupied.
* Service traffic is forwarded to the cluster IP address of the LoadBalancer service through iptables NAT rules, and is further forwarded by kube-proxy to the back-end pods.

## Links

* https://porterlb.io/
* https://github.com/kubesphere/porter/issues/180

## Quickstart

You can start with [a minimal KubeSphere system](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Install Porter on KubeSphere](https://porterlb.io/docs/getting-started/installation/install-porter-on-kubesphere/) once KubeSphere is ready and [Build the Porter Project](https://porterlb.io/docs/building/).

## Newbie-Friendly Issues

* [Add events and logs in key places during service processing](https://github.com/kubesphere/porter/issues/187)
* [Integration with calico, reuse of calico bgp functions](https://github.com/kubesphere/porter/issues/151)

## Potential Mentors

* [Zhengyi Lai](https://github.com/zheng1)
* [Jiong Duan](https://github.com/duanjiong)
