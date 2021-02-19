## Project goal

Multiplex the node ip address as the external ip address of the LoadBalancer service, and forward the traffic to the cluster ip of the service through the iptables nat rule.

## Skills to study/improve

* Golang
* Kubernetes
* Linux network(iptables、ipvs)

## Details

### Background

Previously PorterLB supported two modes to expose Services in K8S, but for users, this was dependent on the underlying environment (e.g. L3 mode requires the switch to support BGP). We can now add some modes to make it easier for users to expose services even in some restricted environments.

### Project details

In the LoadBalancer service, there is a port configuration. We need to select the node from the k8s node whose port is not occupied, and then convert the destination ip address to the service cluster ip through iptables rules, and then the traffic is forwarded by kube-proxy to finally expose the service.

## Links

* https://porterlb.io/
* https://github.com/kubesphere/porter/issues/180

## Quick-start

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). Install [Porter on KubeSphere (Web Console)](https://github.com/kubesphere/porter/blob/master/doc/install-porter-on-kubesphere.md) once KubeSphere is ready. And [Build the Porter Project](https://github.com/kubesphere/porter/blob/master/doc/how-to-build.md).

## Newbie-friendly issues

* [Add events and logs in key places during service processing](https://github.com/kubesphere/porter/issues/187)
* [Integration with calico, reuse of calico bgp functions](https://github.com/kubesphere/porter/issues/151)

## Potential Mentors

* [Zhengyi Lai](https://github.com/zheng1)
* [Jiong Duan](https://github.com/duanjiong)
