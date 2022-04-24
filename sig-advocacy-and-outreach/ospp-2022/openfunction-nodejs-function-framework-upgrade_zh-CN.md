# 项目

OpenFunction 的 Node.js 函数框架升级

## 项目目标

升级现有的 OpenFunction Node.js Function Framework（函数框架），使之对齐 OpenFunction 0.6.0 两大主体功能 —— 函数插件和可观测能力。

## 技术要求

* Node.js
* Kubernetes
* CloudEvent
* OpenFunction
* Cloud Native Buildpacks
* Dapr、Knative（可选）

## 背景知识

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（FaaS，Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

[Dapr](https://dapr.io/) 是一种可移植的、跨平台的事件驱动的运行时，它使开发人员可以轻松构建弹性，无状态和有状态微服务，这些服务运行在云和边缘上，并包含多种语言和开发框架。OpenFunction 将 Dapr 集成其中作为异步函数和同步函数的异步输出的技术支点。

[Knative](https://knative.dev/) 是谷歌开源的 Serverless 架构方案，旨在提供一套简单易用的 Serverless 方案，把 Serverless 标准化。OpenFunction 目前开发符合 Knative 标准的同步函数。

[SkyWalking](https://skywalking.apache.org/) 提供了在许多不同场景下观测和监控分布式系统的解决方案。OpenFunction 将 go2sky（SkyWalking 的 Go 语言代理）捆绑在 OpenFunction 追踪器选项中，以提供分布式追踪、函数性能统计和函数依赖关系图。

## 项目详情

[OpenFunction 0.6.0](https://openfunction.dev/zh/blog/2022/03/25/openfunction-0.6.0-%E5%8F%91%E5%B8%83-faas-%E5%8F%AF%E8%A7%82%E6%B5%8B%E6%80%A7http-%E5%90%8C%E6%AD%A5%E5%87%BD%E6%95%B0%E8%83%BD%E5%8A%9B%E5%A2%9E%E5%BC%BA%E5%8F%8A%E6%9B%B4%E5%A4%9A%E7%89%B9%E6%80%A7/) 的发布带来了许多值得关注的功能，包括函数插件、函数的分布式跟踪、控制自动缩放、HTTP 函数触发异步函数等。同时，异步运行时定义也被重构了。核心 API 也已经从 `v1alpha1` 升级到 `v1beta1`。

0.6.0 版本中有两个重要的功能是基于函数框架的支撑来完成的，它们分别是：

* **函数插件**：在 OpenFunction 的函数 CRD 中，允许用户定义在主体（Main）函数运行前/后执行的插件（Plugin）函数，并在函数运行时依靠函数框架保障插件的运行及其运行关系。您可以参见 [此案例](https://github.com/OpenFunction/samples/blob/cf5e42547ae67b45cf38dd125192a44c6e896131/functions/async/bindings/cron-input-kafka-output/cron-input-kafka-output.yaml#L6) 中的插件定义来初步了解。

* **函数可观测**：第二项重要的功能是 [使用 SkyWalking 为 OpenFunction 提供可观测能力](https://openfunction.dev/zh/docs/best-practices/skywalking-solution-for-openfunction/)。类似的，这些功能也需要函数框架的支持来使得 SkyWalking 可以正确的构建函数关系和追踪链路。

目前 OpenFunction Go Function Framework 是完整支持上述两项功能的，我们期望在本项目中使得 Node.js Function Framework 也具备这两项能力。

## 项目范围

可以先熟悉 OpenFunction Node.js 函数框架，再为该框架新增函数插件和可观测能力支持。

## 项目产出

潜在的成果可能包括：

* 为 Node.js Function Framework 新增函数插件和可观测能力支持
* 为新增功能编写对应的测试用例、样例函数和使用说明
* 产出您关于 OpenFunction、Node.js Functions Framework 的认知与理解

## 链接

* <https://github.com/OpenFunction/OpenFunction>
* <https://github.com/GoogleCloudPlatform/functions-framework>
* <https://buildpacks.io/>
* <https://dapr.io/>

## 快速入门

您可以先 [安装 OpenFunction](https://github.com/OpenFunction/OpenFunction#install) ，然后 [创建一个简单的函数](https://github.com/OpenFunction/OpenFunction#quickstart) 。您可以参考 [OpenFunction Node.js Function Framework](https://github.com/OpenFunction/functions-framework-nodejs) 学习了解目前 Node.js 函数框架的功能和具体实现。

## 导师/联系方式

* [Haili Zhang](https://github.com/webup)
