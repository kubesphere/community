# 项目

使用 iptables 的 NAT 规则暴露 K8s Loadbalancer 服务

## 项目目标

为 [PorterLB](https://porterlb.io/) 提供一个更简单的模式：允许用户使用 Kubernetes 集群节点的 IP 地址和服务端口来暴露 LoadBalancer 服务。

## 技术要求

* Go 语言
* Kubernetes
* Linux network (iptables 和 IPVS 相关技术栈)

## 项目背景

PorterLB 是一款为 Kubernetes 集群暴露 K8s LoadBalancer Service 的插件，方便用户灵活的暴露 K8s 服务。目前 PorterLB 提供了 L2 模式和 BGP 模式两种方式，但是这两种方式都需要额外的配置项（Eip, BgpConf, BgpPeer）。而且 BGP 模式对环境的要求更高，还需要路由器（三层交换机）支持 BGP 协议。

我们希望能提供一个更简单的模式，让用户使用起来也更简单。

## 项目详情

新模式需要支持下面的功能：

* 可以通过 Kubernetes 集群节点的 IP 地址和服务端口直接访问 LoadBalancer Service，而不是使用 NodePort 的方式
* PorterLB 自动选择一个 Kubernetes 集群节点，该节点与该服务对应的端口没有被占用
* Service 的流量通过 iptables 的 NAT 规则转发到 LoadBalancer Service 的 cluster IP 地址，然后由 kube-proxy 进一步转发到后端 pod

## 项目范围

可以先尝试手动配置 iptables 规则，实现类似功能后再尝试在 PorterLB 中集成相应的代码

## 项目产出

- 扩展 PorterLB 的模式，使其用法更简单
- 测试并输出测试报告
- 编写相关文档

## 链接

* https://porterlb.io/
* https://github.com/kubesphere/porter/issues/180

## 快速入门

你可以先从 [在 Kubernetes 上最小化安装 KubeSphere](https://kubesphere.com.cn/docs/quick-start/minimal-kubesphere-on-k8s/) 开始. 安装完集群后可以参考文档 [在 KubeSphere 上安装 PorterLB](https://porterlb.io/docs/getting-started/installation/install-porter-on-kubesphere/)。然后参考文档 [构建 PorterLB](https://porterlb.io/docs/building/)。

## 入门 Issues

* [在处理 Service 的过程中，加入事件和日志](https://github.com/kubesphere/porter/issues/187)
* [集成 Calico，复用 Calico 的 BGP 相关函数](https://github.com/kubesphere/porter/issues/151)

## 导师/联系方式

* [Zhengyi Lai](https://github.com/zheng1)
