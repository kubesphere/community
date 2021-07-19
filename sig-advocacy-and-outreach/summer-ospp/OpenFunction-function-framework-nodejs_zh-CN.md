# 项目

OpenFunction 的 nodejs 函数框架开发

## 项目目标

开发用于处理 nodejs 代码的函数框架，为用户的业务代码提供适用于云原生环境的多种工具套件。

## 技术要求

* Nodejs
* Kubernetes
* CloudEvent
* Dapr
* OpenFunction
* Cloud Native Buildpacks
* Golang、Knative[可选]

## 项目背景

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

[Dapr](https://dapr.io/) 是一种可移植的，serverless的，事件驱动的运行时，它使开发人员可以轻松构建弹性，无状态和有状态微服务，这些服务运行在云和边缘上，并包含多种语言和开发框架。

[Knative](https://knative.dev/) 是谷歌开源的serverless 架构方案，旨在提供一套简单易用的serverless 方案，把serverless 标准化。 

## 项目详情

在当下的 serverless 框架中，事件来源将驱动 serverless 孵化工作负载。从而就要求用户应用可以支持多种驱动来源，如 HTTP、CloudEvent、Dapr bindings 等。为了减少用户编写应用的成本，OpenFunction 需要为用户函数提供用于适配 serverless 生态的工具套件。

此工具套件需要具备两个主要能力：

- Main 函数模板渲染

  在 OpenFunction 的函数构建过程中，函数构建器将相关的 crd 资源属性及环境变量传入 Main 函数模板，渲染后产出最终应用负载中的代码。

- 函数工具套件

  用于为用户函数提供适配 serverless 生态的工具套件，如支持 HTTP、CloudEvent、Dapr bindings 等驱动。

目前我们的函数构建器使用了 [GoogleCloudPlatform 的 functions-framework](https://github.com/GoogleCloudPlatform/functions-framework) 。该 functions-framework 目前不支持 HTTP、CloudEvent 之外的驱动。

我们希望：

1. 产出可以适配 HTTP、CloudEvent、Dapr bindings 的 nodejs 函数框架

## 项目范围

可以先熟悉 OpenFunction ，再使用 OpenFunction/builder 构建你的函数并成功运行。

## 项目产出

潜在的成果可能包括：

* 完成可以处理 nodejs 代码的函数框架；
* 编写 nodejs 函数框架的测试案例、使用说明
* 产出你关于 OpenFunction 、functions-framework 的认知与理解

## 链接

* https://github.com/GoogleCloudPlatform/functions-framework
* https://dapr.io/
* https://github.com/OpenFunction/OpenFunction
* https://buildpacks.io/

## 快速入门

你可以先 [安装 OpenFunction](https://github.com/OpenFunction/OpenFunction#install) ，然后 [创建一个简单的函数](https://github.com/OpenFunction/OpenFunction#quickstart) 。你可以参考 [gcp 的 functions-framework](https://github.com/GoogleCloudPlatform/functions-framework) 学习关于函数框架的原理 。

## 入门 Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/labels/good%20first%20issue)

## 导师/联系方式

* [Benjamin Huo](https://github.com/benjaminhuo)

* [Fang Tian](https://github.com/tpiperatgod/) ，<fangtian@yunify.com>
