# 项目

KubeSphere Sharing Secret 插件开发

## 项目目标

在 KubeSphere 可插拔框架的基础之上开发 Sharing Secret 插件。

## 技术要求

* React
* Helm
* Docker
* Kubernetes
* Golang(可选)

## 项目背景

Kubernetes 中 secret 是 namespace 层级的资源，在实际的使用过程中经常会遇到需要在多个 namespace 之间共享 secret 的需求，在多个 namesapce 下去创建 secret 或是逐一编辑，会带来许多重复工作。

为此我们需要增加一个可以在多个 namespace 之间共享 secret 的功能实现，该功能可以作为 KubeSphere 的一个插件进行集成。

## 项目详情

KubeSphere 4.0 采用了[可插拔架构](https://github.com/kubesphere/community/blob/master/sig-architecture/concepts-and-designs/pluggable-architecture-zh.md)，便于功能拓展与服务集成。

本项目旨在使用 KubeSphere 插件框架，借助 React/Golang 技术栈，构建一个完整的插件应用，该插件允许用户在 KubeSphere 上创建 secret 资源，并在多个 namespace 之间共享，包括但不限于具体的前后端实现。

## 项目产出

* 插件前端实现
* 插件后端实现
* 插件镜像

## 链接

* https://github.com/kubesphere
* https://github.com/kubesphere/dev-guide
* https://kubernetes.io/docs/concepts/configuration/secret/
* https://helm.sh/docs/intro/quickstart/

## 快速入门

首先，你可以从安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。

请参考[插件开发示例](https://github.com/kubesphere-sigs/plugins)，[插件开发文档](https://github.com/kubesphere/community/blob/master/sig-architecture/concepts-and-designs/plugin-development-guide-zh.md)。

## 导师/联系方式

* [hongming](https://github.com/wansir/)
