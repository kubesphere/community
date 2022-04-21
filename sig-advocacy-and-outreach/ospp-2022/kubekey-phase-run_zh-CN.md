# 项目

KubeKey Phase Run 功能开发

## 项目目标

为 KubeKey 提供阶段运行（Phase Run）功能

## 技术要求

* Golang
* Kubernetes
* Linux

## 项目背景

KubeKey 是一个 Kubernetes 集群部署工具，可以实现一键部署 Kubernetes 集群，并且支持 Kubernetes 集群的扩展和维护。但是 KubeKey 流程执行步骤较多流程较长，如果 KubeKey 在执行过程中出现预期外的情况导致执行中断并失败，用户只能排查问题并重新开始执行 KubeKey 。

为此我们需要为 KubeKey 提供阶段运行（Phase Run）功能来帮助用户在排查完问题后，可直接延续之前执行失败的进度手动分阶段执行完剩余流程。

## 项目详情

KubeKey 采用流水线式，模块化的[架构](https://github.com/kubesphere/kubekey/blob/master/docs/developer-guide.md)，方便开发者任意组合、拆分各功能模块。

本项目旨在根据现有的 KubeKey 架构基础上，根据功能划分拆分当前命令流水线，强化各个模块的独立性。可参考 Kubeadm phase run 的效果，最终形成各个功能模块可独立运行，实现阶段运行功能。

## 项目产出

* KubeKey Phase Run 功能
* KubeKey Phase Run 相关命令
* KubeKey Phase Run 测试用例和相关文档
* 产出您关于 KubeKey 的理解

## 链接

* https://github.com/kubesphere/kubekey
* https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-init-phase/

## 快速入门

首先，你可以使用 KubeKey 安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/all-in-one-on-linux/)。

请参考[开发者指南](https://github.com/kubesphere/kubekey/tree/master/docs)。

## 导师/联系方式

* [24sama](https://github.com/24sama/)