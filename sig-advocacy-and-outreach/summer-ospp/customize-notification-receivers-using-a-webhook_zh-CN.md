https://hackmd.io/@kA_hXb92SEWvsiZemHcP5Q/HJLAQ1GL_/edit

## 项目目标

启用  [Notification Manager](https://github.com/kubesphere/notification-manager)  获取通知接收者列表，以便用户可以自定义通知接收者

## 技术要求

* Golang
* REST API
* Kubernetes

## 项目背景

当前，Notification Manager 根据 namespace 的 RoleBindings 确定通知接收者。在这种机制下，某些需要接收通知的用户可能不会收到通知。例如，当用户有权管理 namespace 但不在 namespace 中时，不会将来自 namespace 的通知发送给用户。

我们希望提供一种允许用户自定义通知接收者的机制。

## 项目详情

我们计划将 Sidecar 注入 Notification Manager 部署中，该实现实现了获取接收者列表的逻辑。Sidecar 需要支持以下功能：

* 提供一个接口，用于根据 namespace 获取接收者列表，该接口应具有统一的输入参数和返回值。
* 缓存接收者列表以减少资源消耗。

## 项目范围

TODO

## 项目产出

TODO

## 链接

* https://github.com/kubesphere/notification-manager
* https://kubesphere.com.cn/en/docs/cluster-administration/cluster-wide-alerting-and-notification/notification-manager/

## 快速入门

You can start with a [minimal KubeSphere system](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). 

## 导师/联系方式

* [Benjamin Huo](https://github.com/benjaminhuo)
* [Wanjun Lei](https://github.com/wanjunlei)
