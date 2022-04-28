# 项目

KubeSphere-DevOps 对接 FluxCD

## 项目目标

* 对接 FluxCD
* 实现 FluxCD 部署过程图形化操作

## 技术要求

* Golang
* Kubernetes
* FluxCD
* React（前端）

## 项目背景

`KubeSphere-DevOps` 是一个云原生 DevOps 工具, 当前已经集成了流水线（基于 Jenkins）, 持续部署（基于 Argo CD）。

`FluxCD` 是一个 CNCF 孵化云原生 CD 工具, 是可以用于支持实现 GitOps 的工具集，用于使 `Kubernetes` 集群与配置源（Git 仓库、Helm、Kustomize 等等）保持同步，并且可以在配置源更新后自动同步配置，面向 `Kubernetes` 的渐进式交付解决方案。

2022 年 8 月, Fulx 官方发布了 [GitOps is about to get better with Flux v2](https://www.weave.works/blog/gitops-with-flux-v2) 宣告了从 Flux 到 Flux v2 的交替。

`KubeSphere` 当前拥有强大的多集群管理与应用负载管理能力，基于 `KubeSphere` 上述的能力，通过对接 `FluxCD` 增强 `KubeSphere` 多集群应用发布与管理能力。 

## 项目详情

`KubeSphere-DevOps` 已经在 3.3 版本中完成了与`Argo CD`的对接，在 CD 选择上，对接 `FluxCD` 可以给用户更多的选择、适应不同的应用场景。

项目主要目标为完成对接 `FluxCD` 各个组件:

* `Source Controller`：主要作用是为其他工具提供通用的接口用于获取配置源；
* `Kustomize Controller`：使用声明式的方式管理 `Kustomize`；
* `Helm Controller`：使用声明式的方式管理 `Helm Release`；
* `Notification Controller`：通知服务，可以通过HTTP的方式接收时间并根据事件等级及设计资源将事件分发到外部系统（Slack、Webhook 等）；
* `Image Automation Controllers`：用于根据镜像变更自动更新配置源。


我们希望:

* 在 `KubeSphere-DevOps` 增加对 `FluxCD` 相关资源配置、变更操作的 API；
* 在 `KubeSphere-DevOps` 控制台实现 `FluxCD` 多集群部署的便捷配置；
* 在 `KubeSphere-DevOps` 增加对部署状态管理的的 API。

## 项目产出

### 掌握 `DevOps` `FluxCD` 相关知识与理解

* 掌握 `DevOps` 相关的知识，包括但不限于：什么是 `DevOps`, 为什么需要 `DevOps`，`DevOps` 实践

* 掌握 `FluxCD` 相关知识:  各个 `Controller` 所对应的资源含义与使用

### 完成 `KubeSphere-DevOps` 与 `FluxCD` 的对接
#### Source Controller 

完成基于 `Source Controller` 所支持的配置源管理与对接，包括: 

* Git Repository
* Helm Charts
* Helm Repositories
* Object Storage Buckets

完成上述资源在控制平面的管理、多集群的应用与更新。

#### Kustomize Controller

完成 Kustomize 管理 API、多集群应用差异化配置设计与实现。

#### Helm Controller

完成 Helm 管理 API、*多集群应用差异化配置* 设计与实现。

#### Notification Controller

基于`Notifcation Controller`  完成应用发布状态的管理与展示。

#### Image Automation Controllers

基于 `Image Automation Controllers` 相关组件完成应用自动化更新的配置与管理及状态更新。

## 链接

* [FluxCD](https://fluxcd.io/)
* [ks-devops](https://github.com/kubesphere/ks-devops)
* [helm](https://helm.sh/)
* [kustomize](https://kustomize.io/)

## 导师

[LXM](https://github.com/lxm)