
# 项目

cluster-api-kubekey-provider 升级

## 项目目标

使⽤框架与任务分离架构升级 cluster-api-kubekey-provider。

## 技术要求

- 后端语⾔：golang，shell
- 流程语法：ansible，pongo2
- Kubernenetes 集群：Kubernetes，helm，cluster-api，autoscaler

## 项目背景

KubeKey 已经集成⼊ cluster-api（cluster-api-kubekey-provider），但由于 Kubernetes 集群组件的多样性和丰富性，当前 KubeKey 覆盖到完整的集群组件使得 KubeKey 项⽬愈发庞⼤，故采⽤框架与任务分离的⽅式对 Kubernetes 的管理任务进⾏解耦，相应的 cluster-api-kubekey-provider 也需要进⾏升级。

## 项目详情

核⼼框架采⽤ golang 开发。核⼼包尽量⼩⽽简洁。⽀持使⽤命令⾏的模式和 crd 的模式进⾏驱动。

任务模板采⽤ yaml 的模式进⾏编写。任务可放置到本地⽬录，远程 git 仓库。任务可实现⽆限扩展。

## 开发内容

核⼼框架中，实现 cluster-api 的接⼝，集成 cluster-api 的标准化 api，并⽤于驱动任务模板执⾏。实现 autoscaler 的⾃动扩缩容。

任务模板中，设计满⾜ KubeKey 框架的任务流程，对 Kubernetes 集群进⾏管理，包含节点的新增、删除。

## 项目产出

- 基于框架与任务分离架构的 KubeKey ，开发⼀个符合 cluster-api 标准的集群⽣命周期管理控制器
- 输出操作指南和文档

## 导师联系方式

- [刘健](https://github.com/ImitationImmortal)
- 联系邮箱：blacktiledhouse@gmail.com