## 项目

OpenELB EIP 分配到 Namespace



## 项目目标

实现 OpenELB EIP 分配到匹配的一个或者多个 Namespace 的功能



## 技术要求
- Golang

- Kubernetes

- OpenELB

  

## 项目背景
OpenELB 是一个开源的云原生负载均衡器实现，可以在基于裸金属服务器、边缘以及虚拟化的 Kubernetes 环境中使用 LoadBalancer 类型的 Service 对外暴露服务。

在云服务环境中的 Kubernetes 集群里，通常可以用云服务提供商提供的负载均衡服务来暴露 Service，但是在本地没办法这样操作。而 OpenELB 可以让用户在裸金属服务器、边缘以及虚拟化环境中创建 LoadBalancer 类型的 Service 来暴露服务，并且可以做到和云环境中的用户体验是一致的。



## 项目详情

OpenELB EIP 是 OpenELB 为 Loadbalancer 类型 Service 分配地址的 IP 池，现版本的 OpenELB 支持设置默认 EIP，而默认 EIP相当于分配到所有的 Namespace。为了更细粒度的 IP 池的管理、分配，可以通过创建一个包含 IP 掩码比较小或者指定 IP 段的 EIP，并绑定到指定 Namespace 的方式实现。同时应该考虑不同 EIP 优先级的问题。



## 项目产出

- 完成相应功能的开发

- 完成兼容性测试

- 提供文档的说明

  

## 快速入门

您可以通过阅读 [OpenELB Overview](https://openelb.io/docs/overview/)来快速了解 OpenELB 的基础能力。

您还可以动手 [安装 OpenELB](https://openelb.io/docs/getting-started/installation/)，并使用简单的 Layer2 模式熟悉一下OpenELB的基本用法[Use OpenELB in Layer 2 Mode](https://openelb.io/docs/getting-started/usage/use-openelb-in-layer-2-mode/)；并参考 [Configure IP Address Pools Using Eip](https://openelb.io/docs/getting-started/configuration/configure-ip-address-pools-using-eip/) 学习目前 EIP 的更多细节，同时也可以结合 [OpenELB 代码](https://github.com/openelb/openelb)来学习具体的实现。



## 导师/联系方式

-   [renyunkang](https://github.com/renyunkang/)
