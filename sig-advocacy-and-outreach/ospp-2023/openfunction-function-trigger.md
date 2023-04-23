# 项目

OpenFunction 函数触发器

## 项目目标

设计 OpenFunction 函数触发模式，提高用户的函数触发体验。

## 技术要求

* Kubernetes
* Dapr
* OpenFunction
* Keda
* Golang、Knative[可选]

## 背景知识

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

[Dapr](https://dapr.io/) 是一种可移植的，serverless 的，事件驱动的运行时，它使开发人员可以轻松构建弹性，无状态和有状态微服务，这些服务运行在云和边缘上，并包含多种语言和开发框架。

[Knative](https://knative.dev/) 是谷歌开源的 serverless 架构方案，旨在提供一套简单易用的 serverless 方案，把 serverless 标准化。 

## 项目详情

当前 OpenFunction Function CRD 在配置和 reconciliation 逻辑上存在一定的复杂度，比如函数的输入输出配置以及同步函数和异步函数的差异性配置。本提案旨在简化 OpenFunction 的核心架构，提高用户对项目价值的理解，降低学习成本，消除使用上的割裂感。

我们将统一异步函数与同步函数的配置，通过新增函数触发器及相关配置，区分底层函数的实现逻辑。rest API 的触发方式将生成原先的同步函数，其他触发方式将生成原先的异步函数。

同时，我们尝试使用为 OpenFunction 新增基于 keda-http-addon 实现的同步函数方案，这有助于统一 OpenFunction 核心架构，提高一致性。

好处：

- 消除使用上的割裂感
- 精简 OpenFunction 核心架构

关键路径：

1. 调整 Function CRD 的配置
2. 验证使用 Keda-http-addon 配合 Dapr 实现同步函数的可能性
3. 完成 OpenFunction 架构上的调整（部署、使用等）

## 项目产出

潜在的成果可能包括：

- 为 OpenFunction 新增触发器特性
- 为 OpenFunction 新增基于 keda-http-addon 的同步函数引擎（进阶）
- 优化 OpenFunction 核心架构（进阶）

## 链接

* https://dapr.io/
* https://github.com/OpenFunction/OpenFunction
* https://github.com/kedacore/http-add-on

## 快速入门

你可以先 [安装 OpenFunction](https://openfunction.dev/docs/getting-started/) ，然后 [创建一个简单的函数](https://openfunction.dev/docs/getting-started/quickstarts/) 。

接着你可以学习 [Dapr](https://docs.dapr.io/) 和 [Keda](https://keda.sh/) 这两个项目，从 [Dapr Quickstarts](https://docs.dapr.io/getting-started/quickstarts/) 和 [Keda samples](https://github.com/kedacore/samples) 入门会比较合适。

之后你可以学习 [http-add-on](https://github.com/kedacore/http-add-on) 项目，它是 Keda 提供的用于处理同步请求的伸缩器。

## 导师/联系方式

* [Fang Tian](https://github.com/tpiperatgod/) ，<fangtian@kubesphere.io>