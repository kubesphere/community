# 项目

集成 Gatekeeper

## 项目目标

将 [Gatekeeper](https://github.com/open-policy-agent/gatekeeper) 集成到 KubeSphere，支持一些基础、通用的准入策略配置。

## 技术要求

* React
* Golang
* OpenAPI
* Open Policy Agent
* Kubernetes

## 项目背景

Kubernetes 允许通过 admission webhooks 将策略决策与 API 服务的内部工作解耦，每当创建、更新或删除资源时都会执行这些策略。Gatekeeper 提供了一个 validating webhook，它强制执行由 Open Policy Agent 执行的基于 CRD 的策略，我们可以在 KubeSphere 集成 Gatekeeper 提供的策略管理功能，通过 CRD 来管理一些常用的规则策略。

## 项目详情

[Open Policy Agent](https://github.com/open-policy-agent/opa), CNCF孵化中的应用于云原生环境的规则策略引擎。
[Gatekeeper](https://github.com/open-policy-agent/gatekeeper), 基于K8s admission webhook 和 OPA 的策略管理工具。

我们希望集成 Gatekeeper 到 KubeSphere 中，管理一些基础的策略，例如：必须使用受信任的镜像仓库、部署的工作负载必须包含必填的控制字段。

## 项目产出

* 在 KubeSphere 安装过程中集成 Gatekeeper
* 完成 Gatekeeper 的基础功能集成 
* 完成兼容性测试

## 链接

* https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/
* https://github.com/open-policy-agent/opa
* https://github.com/open-policy-agent/gatekeeper

## 快速入门

安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。

[安装 Gatekeeper](https://open-policy-agent.github.io/gatekeeper/website/docs/install)。

首先你需要熟悉 KubeSphere 和 Gatekeeper。

## 入门 Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## 导师/联系方式

* [Hongming](https://github.com/wansir/)
* [Roland](https://github.com/rolandma1986/)

