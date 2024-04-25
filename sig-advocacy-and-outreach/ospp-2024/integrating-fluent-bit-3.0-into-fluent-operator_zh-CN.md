# 项目

Fluent Operator  集成 Fluent-bit 3.0

## 项目目标

将 Fluent-bit 3.0 集成到 [Fluent Operator](https://github.com/fluent/fluent-operator) 中开发并集成其部分特性。

## 技术要求

- Golang
- Kubernetes
- Fluent-bit
- Fluentd

## 项目背景

Fluent Bit 已经发布 3.0 版本，提高了性能，增加了许多功能，包括但不限于：

- 高性能：高吞吐量和低资源消耗

- 数据解析

  - 使用我们的解析器转换您的非结构化消息：[JSON](https://docs.fluentbit.io/manual/pipeline/parsers/json)、[Regex](https://docs.fluentbit.io/manual/pipeline/parsers/regular-expression)、[LTSV](https://docs.fluentbit.io/manual/pipeline/parsers/ltsv)和[Logfmt](https://docs.fluentbit.io/manual/pipeline/parsers/logfmt)

- 指标支持：Prometheus 和 OpenTelemetry 兼容

- 可靠性和数据完整性

  - [背压](https://docs.fluentbit.io/manual/administration/backpressure)处理
  - 内存和文件系统中的[数据缓冲](https://docs.fluentbit.io/manual/administration/buffering-and-storage)

- 联网

  - 安全性：内置 TLS/SSL 支持
  - 异步 I/O

- 可插拔架构和[可扩展性](https://docs.fluentbit.io/manual/development/library_api)：输入、过滤器和输出

  - 使用预先存在的插件将几乎任何源连接到几乎任何目的地
  - 可扩展性
    - 用 C 语言编写任何输入、过滤器或输出插件
    - WASM：[WASM 过滤器插件](https://docs.fluentbit.io/manual/development/wasm-filter-plugins)或[WASM 输入插件](https://docs.fluentbit.io/manual/development/wasm-input-plugins)
    - 奖励：[在 Lua 中编写过滤器](https://docs.fluentbit.io/manual/pipeline/filters/lua)或[在 Golang 中编写输出插件](https://docs.fluentbit.io/manual/development/golang-output-plugins)

- [监控](https://docs.fluentbit.io/manual/administration/monitoring)：通过 HTTP 以 JSON 和[Prometheus](https://prometheus.io/)格式公开内部指标

- [流处理](https://docs.fluentbit.io/manual/stream-processing/introduction)：使用简单的 SQL 查询执行数据选择和转换

  使用查询结果创建新的数据流

  - 聚合窗口
  - 数据分析和预测：时间序列预测

- 便携式：可在 Linux、macOS、Windows 和 BSD 系统上运行

集成新版本的 Fluent Bit 有助于增强信息收集能力，使得 Fluent Operator 可以处理更为复杂数据信息。

## 项目详情

随着云原生技术的快速发展，技术的不断迭代，对于日志的采集、处理及转发提出了更高的要求。云原生架构下的日志方案相比基于物理机或者是虚拟机场景的日志架构设计存在很大差别。作为 CNCF 的毕业项目，Fluent Bit 无疑为解决云环境中的日志记录问题的首选解决方案之一。但是在 Kubernetes 中安装部署以及配置 Fluent Bit 都具有一定的门槛，加大了用户的使用成本。

**2019 年 1 月 21 日**，KubeSphere 社区为了满足以云原生的方式管理 Fluent Bit 的需求开发了 **Fluentbit Operator**，并在 2020 年 2 月 17 日发布了 v0.1.0 版本。此后产品不断迭代，在 **2021 年 8 月 4 日** 正式将 Fluentbit Operator 捐献给 Fluent 社区。

Fluentbit Operator 降低了 Fluent Bit 的使用门槛，能高效、快捷的处理日志信息，但是 Fluent Bit 处理日志的能力稍弱，我们还没有集成日志处理工具，比如 Fluentd，它有更多的插件可供使用。基于以上需求，Fluentbit Operator 集成了 Fluentd，旨在将 Fluentd 集成为一个可选的日志聚合和转发层，并重新命名为 **Fluent Operator（GitHub 地址： https://github.com/fluent/fluent-operator）**。我们在 2022 年 3 月 25 日 Fluent Operator 发布了 v1.0.0 版本，2023 年2 月 3 日 发布 v2.0.0 版本，并将在以后的时间里继续迭代 Fluent Operator，增加更多的功能与亮点。

使用 Fluent Operator 可以灵活且方便地部署、配置及卸载 Fluent Bit 以及 Fluentd。同时, 社区还提供支持 Fluentd 以及 Fluent Bit 的海量插件，用户可以根据实际情况进行定制化配置。官方文档提供了详细的示例，极易上手，大大降低了 Fluent Bit 以及 Fluentd 的使用门槛。

## 项目产出

- 完成 Fluent Operator 中 Fluent-bit 3.0 的集成 
- 根据需要和紧急情况有选择的适配 Fluent-bit 3.0 的部分特性
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
- 联系邮箱：995729579@qq.com

  