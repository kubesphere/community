# 项目

Notification Manager 发送通知到 pushover

## 项目目标

使 Notification Manager 可以发送通知消息到 pushover。

## 技术要求

- Golang
- REST API
- Kubernetes

## 项目背景

Notification Manager 用于在多租户 K8s 环境下管理通知。Notification Manager 从不同的渠道接收告警消息，然后通过各种的渠道，包括钉钉，邮件，企业微信，slack，webhook，发送给租户。

Pushover 是用于发送和接收推送通知的平台。在服务器端，它提供了一个 HTTP API，用于接收通知消息，并传递到可通过用户或组寻址的设备。在设备方面，iOS，Android 和桌面客户端会接收这些推送通知，将其显示给用户，然后将其存储以供离线查看。

 我们希望 Notification Manager 可以发送通知消息到 pushover，然后由 pushover 将通知推送给用户。

## 项目详情

Pushover 使用简单的 REST API 版本来接收消息并将其广播到运行 pushover 客户端的设备。使用 Pushover 的 API 可以很便捷的实现用户注册过和消息处理，Pushover 的 API 没有复杂的身份验证机制。可以使用几乎每种语言甚至命令行提供的标准 HTTP 库，而无需任何自定义模块或额外的依赖项。

我们可以通过调用 Pushover 来实现发送通知消息到 pushover 。

## 项目产出

- 扩展 Notification Manager CRD 定义，使其支持 pushover
- 实现 Notification Manager 发送通知消息到 pushover
- 测试并输出测试报告
- 编写相关文档

## 链接

- https://github.com/kubesphere/notification-manager
- https://pushover.net/
- https://pushover.net/api

## 快速入门

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/).

## 导师/联系方式

- [benjaminhuo](https://github.com/benjaminhuo)
- [lei](https://github.com/wanjunlei)

