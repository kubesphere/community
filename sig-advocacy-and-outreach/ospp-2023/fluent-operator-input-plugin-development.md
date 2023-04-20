# 项目

Fluent Operator Collector 输入组件开发

## 项目目标

完成 [Fluent Operator](https://github.com/fluent/fluent-operator) 中多个输入插件的开发并集成到 Fluent Operator 中。

## 技术要求

- Golang
- Kubernetes
- Fluent-bit
- Fluentd

## 项目背景

 Fluent Operator 支持 Fluentd 以及 Fluent Bit 的许多插件，已集成 Fluent Bit 的七个输入组件，但是 Fluent Bit 扩展性强，插件丰富，仍有许多插件尚未集成到 Fluent Operator 中，包括以下输入插件（参考 https://github.com/fluent/fluent-operator/issues/304#issuecomment-1338661126）：

- https://docs.fluentbit.io/manual/pipeline/inputs/opentelemetry
- https://docs.fluentbit.io/manual/pipeline/inputs/collectd
- https://docs.fluentbit.io/manual/pipeline/inputs/forward
- https://docs.fluentbit.io/manual/pipeline/inputs/http
- https://docs.fluentbit.io/manual/pipeline/inputs/mqtt
- https://docs.fluentbit.io/manual/pipeline/inputs/nginx
- https://docs.fluentbit.io/manual/pipeline/inputs/statsd
- https://docs.fluentbit.io/manual/pipeline/inputs/syslog
- https://docs.fluentbit.io/manual/pipeline/inputs/tcp

增加多种输入插件有助于增强 Fluent Bit 的信息收集能力，增强 Fluent Operator 处理更为复杂数据信息的能力。

## 项目详情

随着云原生技术的快速发展，技术的不断迭代，对于日志的采集、处理及转发提出了更高的要求。云原生架构下的日志方案相比基于物理机或者是虚拟机场景的日志架构设计存在很大差别。作为 CNCF 的毕业项目，Fluent Bit 无疑为解决云环境中的日志记录问题的首选解决方案之一。但是在 Kubernetes 中安装部署以及配置 Fluent Bit 都具有一定的门槛，加大了用户的使用成本。

**2019 年 1 月 21 日**，KubeSphere 社区为了满足以云原生的方式管理 Fluent Bit 的需求开发了 **Fluentbit Operator**，并在 2020 年 2 月 17 日发布了 v0.1.0 版本。此后产品不断迭代，在 **2021 年 8 月 4 日** 正式将 Fluentbit Operator 捐献给 Fluent 社区。

Fluentbit Operator 降低了 Fluent Bit 的使用门槛，能高效、快捷的处理日志信息，但是 Fluent Bit 处理日志的能力稍弱，我们还没有集成日志处理工具，比如 Fluentd，它有更多的插件可供使用。基于以上需求，Fluentbit Operator 集成了 Fluentd，旨在将 Fluentd 集成为一个可选的日志聚合和转发层，并重新命名为 **Fluent Operator（GitHub 地址： https://github.com/fluent/fluent-operator）**。我们在 2022 年 3 月 25 日 Fluent Operator 发布了 v1.0.0 版本，2023 年2 月 3 日 发布 v2.0.0 版本，并将在以后的时间里继续迭代 Fluent Operator，增加更多的功能与亮点。

使用 Fluent Operator 可以灵活且方便地部署、配置及卸载 Fluent Bit 以及 Fluentd。同时, 社区还提供支持 Fluentd 以及 Fluent Bit 的海量插件，用户可以根据实际情况进行定制化配置。官方文档提供了详细的示例，极易上手，大大降低了 Fluent Bit 以及 Fluentd 的使用门槛。

## 项目产出

- 完成 Fluent Operator 的多个输入组件的开发 
- 完成兼容性测试

## 链接

- https://github.com/fluent
- https://github.com/fluent/fluent-operator
- https://github.com/kubesphere-sigs/fluent-operator-walkthrough
- https://docs.fluentbit.io/manual/pipeline/inputs

## 快速入门

首先，你可以从安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。然后，当 KubeSphere 启动成功后可以通过 [Fluent Operator的 helm 仓库 ](https://github.com/fluent/fluent-operator/tree/master/charts) 安装 Fluent Operator，体验  Fluent Operator 的日志收集功能。

## 入门 Issues

- [Fluent-Operator area newbie-friendly issues](https://github.com/fluent/fluent-operator/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22)

## 导师/联系方式

- [wenchajun](https://github.com/wenchajun)

  