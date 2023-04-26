## 项目名称
基于 Shipwright+Buildpacks 改造 KubeSphere-S2I

## 项目目标
- KubeSphere 上基于 Shipwright+Buildpacks 的 SourceToImage 功能

## 技术要求
- Golang
- Kubernetes
- Buildpacks
- Shipwright 
- React（前端）

## 项目背景
`Source-to-image (S2I)` 是一个工具箱和工作流，用于直接输入源代码然后打包成可运行程序到 Docker 镜像的工具，在用户不需要了解 Dockerfile 的情况下方便构建镜像。它是通过将源代码放入一个负责编译源代码的 Builder image 中，自动将编译后的代码打包成 Docker 镜像。

`Buildpacks` 是基于云原生的容器镜像构建技术，它支持现代语言生态系统，对开发者屏蔽了应用构建、部署的细节，如选用哪种操作系统、编写适应镜像操作系统的处理脚本、优化镜像大小等等，并且会产出 OCI 容器镜像，可以运行在任何兼容 OCI 镜像标准的集群中。

`Shipwright` 是一个可扩张的框架，用来在 Kubernetes 上构建容器镜像；支持众多流行的用于构建容器镜像的工具，比如 Kaniko、Cloud Native Buildpacks、Buildah等。 

`KubeSphere-DevOps` 是 Kubesphere 上的一个云原生 DevOps 工具, 当前已经集成了流水线（基于 Jenkins），持续部署（基于 Argo CD）。

## 项目详情

`S2I` 是 `Kubesphere` 上的非常早期的一个项目，它是基于 `Docker in Docker` 开发的，这种方式强依赖于 Docker，在一些没有 Docker 的环境无法使用，不够优雅；也有一定的安全问题；虽然 S2I 是 DevOps 的一部分，但是在 KubeSphere 前端页面并没有在 DevOps Tab 页下。

此项目的主要目标是基于最新的容器镜像构建技术 Buildpacks 改造 S2I 并统一整合到 DevOps Tab 页：

- 掌握 K8S、Buildpacks、Shipwright、React、S2I/DevOps in kubeSphere 等知识；
- 构建多种编程语言的基础 Buildpacks builder；
- 基于 Shipwright+Buildpacks 构建新 S2I 服务+安装包；
- 需要支持用户自定义 Buildpacks builder；
- 改造 Kubesphere console 前端，把 S2I 服务整合到 DevOps Tab 页；

## 项目产出
- 多种编程语言的基础 Buildpacks `builder`
- 新 S2I 服务（包含前端） + 此服务的 helm 安装包

## 链接
- [Kubesphere-S2I](https://kubesphere.io/zh/docs/v3.3/project-user-guide/image-builder/source-to-image/)
- [Shipwright](https://shipwright.io/docs/)
- [Buildpacks](https://buildpacks.io/docs/)
- [Kubesphere-DevOps](https://github.com/kubesphere/ks-devops)
- [helm](https://helm.sh/)

## 导师
[yudong](https://github.com/yudong2015)






