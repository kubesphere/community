# 开源之夏 2022 - OpenFunction 弹性应用运行时

## 项目目标

## 技术要求

- [Kubernetes](https://github.com/kubernetes/kubernetes)
- [OpenFunction](https://github.com/OpenFunction/OpenFunction)
- [Dapr](https://github.com/dapr/dapr)
- [Keda](https://github.com/kedacore/keda)
- Golang

## 项目背景

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

OpenFunction 作为一个 FaaS 平台，实现了对“函数”这一基础业务单元的生命周期管理。在设计中我们使用到了用于完成“函数”到“应用”的 OCI 镜像构建的组件 Shipwright（以及用于完成构建流水线的 Tekton）；用于负载同步函数的引擎 Knative；用于实现事件驱动机制的 KEDA；用于实现应用分布式响应能力的 Dapr 和用于实现“函数”入口机制的 Ingress Nginx。

Dapr 是一个可移植的、事件驱动的运行时，它使任何开发人员能够轻松构建出弹性的、无状态和有状态的应用程序，并可运行在云平台或边缘计算中，它同时也支持多种编程语言和开发框架。

KEDA 允许对事件驱动的 Kubernetes 工作负载进行细粒度的自动缩放（包括从零到零）。 KEDA 作为 Kubernetes Metrics Server，允许用户使用专用的 Kubernetes 自定义资源定义来定义自动缩放规则。

目前， OpenFunction 基于 Dapr + Keda 实现了异步函数运行时。OpenFunction 的异步运行时将代码中调用 Dapr 的部分抽象了出来，用户可以通过简单的配置即可完成对 Dapr 的调用。这种方式减少了新用户学习的成本，但是对于 Dapr 的老用户会有一定的不适应。且会增加原有的 Dapr 应用函数化的成本。因此 OpenFunction 需要一种新的运行时，其可以直接运行 Dapr 应用，同时可以借助 Keda 的能力实现自动伸缩。

## 项目详情

OpenFunction 弹性应用运行时支持直接运行 Dapr 应用，支持设置 Dapr 组件，如果组件不存在，OpenFunction 会自动为应用创建组件。用户可以通过注解实现对 Dapr 的控制。 

OpenFunction 弹性应用运行时支持通过 Keda 实现应用的自动伸缩。

## 项目范围

- [OpenFunction](https://github.com/OpenFunction/OpenFunction)
- [Dapr](https://github.com/dapr/dapr)
- [Keda](https://github.com/kedacore/keda)

## 项目产出

- 详细设计文档
- 代码
- 完成的测试用例和测试代码

## 快速入门

[OpenFunction](https://github.com/OpenFunction/OpenFunction)

Dapr 弹性运行时相关 [issue](https://github.com/OpenFunction/OpenFunction/issues/230)


## 导师/联系方式

- [雷万钧](https://github.com/wanjunlei) wanjunlei@yunify.com
