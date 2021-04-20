# 项目

Expose Loadbalancer Services Using Iptables Nat Rules

## 项目目标

Provide a simple mode of [PorterLB](https://porterlb.io/), which allows users to use the IP address of a Kubernetes cluster node and a service port to expose a LoadBalancer service.

## 技术要求

* Golang
* Kubernetes
* Linux network (iptables and IPVS)

## 项目背景

Currently, PorterLB supports the Layer 2 mode and BGP mode for exposing LoadBalancer services in a Kubernetes cluster. Both the Layer 2 mode and BGP mode require additional configurations (Eip, BgpConf, and BgpPeer), and the BGP mode requires that the router support BGP.

We hope to provide a simple mode of PorterLB so that users can expose LoadBalancer services more easily.

## 项目详情

The new mode needs to support the following features:

* A LoadBalancer service can be accessed directly through the IP address of a Kubernetes cluster node and the service port without using NodePort.
* PorterLB automatically selects a Kubernetes cluster node whose port corresponding to the service port is not occupied.
* Service traffic is forwarded to the cluster IP address of the LoadBalancer service through iptables NAT rules, and is further forwarded by kube-proxy to the back-end pods.

## 项目范围

TODO

## 项目产出

TODO

## 链接

* https://porterlb.io/
* https://github.com/kubesphere/porter/issues/180

## 快速入门

You can start with [a minimal KubeSphere system](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Install Porter on KubeSphere](https://porterlb.io/docs/getting-started/installation/install-porter-on-kubesphere/) once KubeSphere is ready and [Build the Porter Project](https://porterlb.io/docs/building/).

## 入门 Issues

* [Add events and logs in key places during service processing](https://github.com/kubesphere/porter/issues/187)
* [Integration with calico, reuse of calico bgp functions](https://github.com/kubesphere/porter/issues/151)

## 导师/联系方式

* [Zhengyi Lai](https://github.com/zheng1)
* [Jiong Duan](https://github.com/duanjiong)
