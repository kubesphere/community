# 项目

KubeSphere 集成 Tekton

## 项目目标

集成 [Tekton](https://github.com/tektoncd/pipeline) 作为 [KubeSphere](https://github.com/kubesphere/kubesphere/) DevOps 可选的 CI/CD 引擎。

## 技术要求

* Golang
* Kubernetes
* Tekton
* JavaScript[可选]
* Jenkins[可选]

## 项目背景

Tekton 是一个云原生的 CI/CD 项目。相较于 Jenkins，Tekton 可以充分利用 Kubernetes 生态系统的优势。例如，Tekton 一个是无服务器的组件，非常容易扩展。然而，由于 Tekton 缺乏用户友好的用户界面，新用户可能很难操作它。我们希望能充分利用 Tekton 的优势，使其在 KubeSphere 中易于使用。

## 项目详情

目前，Jenkins 是 KubeSphere DevOps 组件的引擎。[Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) 负责将流水线的 CRD 转换为 Jenkins Job。
请考虑[CRD](https://github.com/kubesphere/kubesphere/blob/master/staging/src/kubesphere.io/api/devops/v1alpha3/pipeline_types.go)的兼容性，尽可能让 Jenkins 和 Tekton 共用一个 CRD。

## 项目范围

可以先完成 Tekton 的部署，然后完成 Trigger、Task、Pipeline 的管理，接着是图形化的编辑、运行、查看。在图形化阶段，可以尝试考虑兼容 CRD。

## 项目产出

潜在的成果可能包括

* KubeSphere 部署 Tekton 的的方案
* 多租户下的 Tekton 集成，包括前端和后端
* 日志，以及档案存储解决方案
* 一个包含集成、使用、用户案例的操作文档
* 与 Jenkins 兼容的 CRD

## 链接

* https://tekton.dev/
* http://jenkins.io/
* https://github.com/kubesphere/kubesphere

## 快速入门

你可以从[一个最小化的 KubeSphere](https://kubesphere.io/zh/docs/quick-start/minimal-kubesphere-on-k8s/)开始。KubeSphere 准备好了之后，[启用 DevOps ](https://kubesphere.io/zh/docs/pluggable-components/devops/)组件，并自己探索 KubeSphere DevOps。

先安装 [Tekton Pipelines](https://github.com/tektoncd/pipeline/blob/master/docs/install.md)，然后按照[教程](https://github.com/tektoncd/pipeline/blob/master/docs/tutorial.md)熟悉各种功能!

## 入门 Issues

* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)

## 导师/联系方式

* [Shaowen Chen](https://github.com/shaowenchen/)
* [Rick](https://github.com/LinuxSuRen/)
