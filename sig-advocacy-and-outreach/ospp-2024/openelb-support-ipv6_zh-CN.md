
# 项目

OpenELB 支持 IPV6

## 项目目标

OpenELB 中包含两大组件：controller 和 speaker。
- controller 负责为 service 分配/回收 ip
- speaker 负责将分配的 ip 对外宣告

因此该项目也有两大目标：
- controller 支持 ipv6 的 ipam
- speaker 不同的模式支持 ipv6 的宣告

## 技术要求

- Golang
- Kubernetes
- OpenELB
- Network
- Gobgp
- NDP(Neighbor Discovery Protocol)
- keepalived

## 项目背景

OpenELB 是一个开源的云原生负载均衡器实现，可以在基于裸金属服务器、边缘以及虚拟化的 Kubernetes 环境中使用 LoadBalancer 类型的 Service 对外暴露服务。

在云服务环境中的 Kubernetes 集群里，通常可以用云服务提供商提供的负载均衡服务来暴露 Service，但是在本地没办法这样操作。而 OpenELB 可以让用户在裸金属服务器、边缘以及虚拟化环境中创建 LoadBalancer 类型的 Service 来暴露服务，并且可以做到和云环境中的用户体验是一致的。

## 项目详情

OpenELB EIP 是 OpenELB 为 Loadbalancer 类型 Service 分配地址的 IP 池，现版本的 OpenELB 仅支持 ipv4。[Kubernetes 已经支持 IPv4/IPv6 双栈](https://kubernetes.io/docs/concepts/services-networking/dual-stack/)，且在 1.23 版本之后已经 stable，因此我们也需要支持 ipv6 的 ipam 以及适配speaker的不同模式将分配到的 ip 对外宣告。

## 项目产出

- 完成相应功能的开发
- 完成兼容性测试
- 提供文档的说明

## 快速入门

您可以通过阅读 [OpenELB Overview](https://openelb.io/docs/overview/)来快速了解 OpenELB 的基础能力。
您还可以动手 [安装 OpenELB](https://openelb.io/docs/getting-started/installation/)，并使用简单的 Layer2 模式熟悉一下 OpenELB 的基本用法[Use OpenELB in Layer 2 Mode](https://openelb.io/docs/getting-started/usage/use-openelb-in-layer-2-mode/)；并参考 [Configure IP Address Pools Using Eip](https://openelb.io/docs/getting-started/configuration/configure-ip-address-pools-using-eip/) 学习目前 EIP 的更多细节，同时也可以结合 [OpenELB 代码](https://github.com/openelb/openelb)来学习具体的实现。

## 导师联系方式

- [renyunkang](https://github.com/renyunkang/)
- 联系邮箱：rykren1998@gmail.com