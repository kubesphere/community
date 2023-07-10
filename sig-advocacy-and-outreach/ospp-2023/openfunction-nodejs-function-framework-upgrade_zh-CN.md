## 项目

OpenFunction 的 Node.js 函数框架支持 Dapr 状态管理

## 项目目标

升级现有的 OpenFunction Node.js Functions Framework（函数框架），使之支持在函数中使用 Dapr 状态管理的能力。

## 技术要求

- Node.js
- Kubernetes
- KinD
- OpenFunction
- Dapr

## 背景知识

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（FaaS，Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

[Dapr](https://dapr.io/) 是一种可移植的、跨平台的事件驱动的运行时，它使开发人员可以轻松构建弹性，无状态和有状态微服务，这些服务运行在云和边缘上，并包含多种语言和开发框架。OpenFunction 将 Dapr 集成其中作为异步函数和同步函数的异步输出的技术支点。

[KinD](https://kind.sigs.k8s.io/) 是一个在本地计算机上运行 Kubernetes 集群的工具，它使用 Docker 容器作为节点来运行 Kubernetes 控制平面和工作负载。使用 KinD，可以在本地以及 CI/CD 环境中快速轻松地创建 Kubernetes 集群，进行测试和开发。

## 项目详情

目前，OpenFunction 支持 Dapr [Pub/Sub](https://docs.dapr.io/reference/components-reference/supported-pubsub/) 和 [Bindings](https://docs.dapr.io/reference/components-reference/supported-bindings/) 构建块，[状态管理](https://docs.dapr.io/reference/components-reference/supported-state-stores/) 是另一个对有状态函数有用的构建块，使用状态存储组件，可以构建有状态的、长期运行的函数来保存和检索它们的状态。

当前最新的 OpenFunction 的基建服务 [已经支持](https://github.com/OpenFunction/OpenFunction/pull/427) 状态管理能力，我们期望在本项目中使 Node.js 函数支持 [这项能力](https://github.com/OpenFunction/OpenFunction/pull/426)。

同时，我们期望您可以参照 [Go Functions Framework](https://github.com/OpenFunction/functions-framework-go) 实现基于 KinD 的端到端自动化测试，进一步提升 Node.js 函数框架的功能鲁棒性。

## 项目产出

潜在的成果可能包括：

- 为 Node.js 函数框架新增状态管理能力支持
- 为新增的状态管理功能编写对应的测试用例、样例函数和使用说明
- 为 Node.js Functions Framework 项目添加基于 KinD 的端到端测试框架及用例

## 快速入门

您可以通过阅读 [OpenFunction Talks](https://github.com/webup/openfunction-talks) 来快速了解 OpenFunction 和 Node.js 函数框架的基础能力。

您还可以动手 [安装 OpenFunction](https://github.com/OpenFunction/OpenFunction#install) ，然后 [创建一个简单的函数](https://github.com/OpenFunction/OpenFunction#quickstart) ；并参考 [OpenFunction Node.js Functions Framework](https://github.com/OpenFunction/functions-framework-nodejs) 学习了解目前 Node.js 函数框架的功能和具体实现。

## 导师/联系方式

- [Haili Zhang](https://github.com/webup)
