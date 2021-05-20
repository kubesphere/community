# 项目

OpenFunction 的函数构建器开发

## 项目目标

开发并优化函数构建器，使其可以识别 Python、Nodejs、Java、PHP（可选）、Rust（可选）语言，并将函数构建成可以运行在 OpenFunction 中的应用镜像。

## 技术要求

* Golang
* Kubernetes
* Tekton
* Cloud Native Buildpacks
* OpenFunction
* Python、Nodejs、Java、PHP、Rust[均可选]

## 项目背景

[OpenFunction](https://github.com/OpenFunction/OpenFunction) 是一个云原生的开源函数即服务（Functions-as-a-Service）平台，旨在让用户专注于他们的业务逻辑，而不必担心底层运行环境和基础设施。用户只需要以函数的形式提交业务相关的源代码，即可将服务按需运行在集群中。

[Tekton](https://github.com/tektoncd) 是一个云原生的 CI/CD 项目。

[Cloud Native Buildpacks](https://github.com/buildpacks) 是一个云原生的 OCI 标准镜像制作工具。（以下简称 Buildpacks ）

## 项目详情

OpenFunction 的 builders 组件集成了 Tekton 与 Buildpacks ，用于完成将用户提交的函数代码制作成可以运行在 Kubernetes 中的应用负载镜像这一部分工作。

Tekton 负责编排整个由代码到应用镜像的制作过程，包含：*拉取镜像*、*准备环境变量*、*使用 Buildpacks 制作镜像*、*输出镜像到指定仓库* 等几个主要步骤。

Buildpacks 负责识别代码的语言类型，然后准备好相关的编译环境，再将代码通过模板渲染为可运行的应用。

构建器的工作内容描述：

![build diagram](https://buildpacks.io/docs/concepts/operations/build.svg)

目前我们的构建器项目地址为：[OpenFunction/builder](https://github.com/OpenFunction/builder) 。构建器的现状参考这里：[Status](https://github.com/OpenFunction/builder#status) 。

我们希望：

1. 它可以支持更多的主流语言（及更多的语言版本）
2. 可以优化代码构建的策略、减少代码构建的时间

## 项目范围

可以先熟悉 OpenFunction ，再使用 OpenFunction/builder 构建你的函数并成功运行。

## 项目产出

潜在的成果可能包括：

* 完成新的语言构建器制作，包括不限于：1. PHP 语言构建器；2. Rust 语言构建器；
* 优化现有语言构建器，包括不限于：1. 提供更多版本支持；2. 构建策略优化；
* 编写语言构建器的测试案例、使用说明
* 产出你关于 OpenFunction 、Tekton 、Buildpacks 的认知与理解

## 链接

* https://tekton.dev/
* https://buildpacks.io/
* https://github.com/OpenFunction/OpenFunction
* https://github.com/OpenFunction/builder

## 快速入门

你可以先 [安装 OpenFunction](https://github.com/OpenFunction/OpenFunction#install) ，然后 [创建一个简单的函数](https://github.com/OpenFunction/OpenFunction#quickstart) 。接着尝试构建自己的函数构建器，参考 [go1.15](https://github.com/OpenFunction/builder/tree/main/builders/go115#build-builder-of-go-version-115) 。

## 入门 Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/labels/good%20first%20issue)

## 导师/联系方式

* [Benjamin Huo](https://github.com/benjaminhuo)

* [Fang Tian](https://github.com/tpiperatgod/) ，<fangtian@yunify.com>
