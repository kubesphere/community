# 项目

OpenELB BGP策略开发

## 项目目标

目前 OpenELB 支持BGP协议。但是对BGP策略目前还不支持。
因此 OpenELB 底层支持的BGP协议的基础上，增加OpenELB对BGP的各种策略支持。

## 技术要求

* golang
* Helm
* Docker
* Kubernetes
* BGP


## 项目背景

OpenELB 项目是为物理机（Bare-metal）、边缘（Edge）和私有化环境设计的负载均衡器插件，可作为 Kubernetes、K3s、KubeSphere 的 LB 插件对集群外暴露 `LoadBalancer` 类型的服务

## 项目详情

OpenELB 采用标准的 gobgp 来发布路由，这样做的好处如下

- 开发成本低，且有 gobgp 社区支持
- 可以利用 gobgp 丰富特性
- 通过 BgpConf/BgpPeer CRD 动态配置 gobgp，用户无需重启 OpenELB 即可动态加载最新的配置信息
- gobgp 作为 lib 使用时， 社区提供了基于 protobuf 的 API， OpenELB 在实现 BgpConf/BgpPeer CRD 时也是参照该 API，并保持兼容
- OpenELB 也提供 status 用于查看 BGP neighbor 配置，状态信息丰富

目前的不足支持
- gobgp支持各种丰富[策略](https://github.com/osrg/gobgp/blob/master/docs/sources/policy.md),但是OpenELB目前没有对接gobgp的策略。导致OpenELB在BGP协议模式下。并不能很好的控制路由宣告。


## 项目产出

* OpenELB 对BGP 策略支持


## 链接

* https://github.com/openelb/openelb/
* https://openelb.github.io/
* https://github.com/osrg/gobgp/blob/master/docs/sources/policy.md

## 快速入门

首先，你可以从安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。
然后，创建一个Deployment和一个Service，Service暴露方式选择LoadBalancer.
接着，尝试安装 [OpenELB](https://openelb.github.io/docs/getting-started/installation/install-openelb-on-kubernetes/). 体验LoadBalancer暴露方式与NodePort,Ingress的不同之处

## 导师/联系方式

* [chaunceyjiang](https://github.com/chaunceyjiang/)
