# Project

Integrating Fluent-bit 3.0 into Fluent Operator

## Project Goal

Integrate Fluent-bit 3.0 into Fluent Operator, develop and integrate some of its features.

## Skills to Learn/Improve

- Golang
- Kubernetes
- Fluent-bit
- Fluentd

## Background

Fluent Bit has released version 3.0, which improves performance and introduces many new features, including but not limited to:

- High performance: High throughput and low resource consumption

- Data parsing

  - Use our parser to convert your unstructured messages: [JSON](https://docs.fluentbit.io/manual/pipeline/parsers/json)、[Regex](https://docs.fluentbit.io/manual/pipeline/parsers/regular-expression)、[LTSV](https://docs.fluentbit.io/manual/pipeline/parsers/ltsv) and [Logfmt](https://docs.fluentbit.io/manual/pipeline/parsers/logfmt)

- Metrics support: Prometheus and OpenTelemetry compatible

- Reliability and data integrity

  - [Backpressure handling](https://docs.fluentbit.io/manual/administration/backpressure)
  - [Data buffering](https://docs.fluentbit.io/manual/administration/buffering-and-storage) in memory and file systems

- Networking

  - Security: Built-in TLS/SSL support
  - Asynchronous I/O

- Pluggable architecture and [scalability](https://docs.fluentbit.io/manual/development/library_api): inputs, filters, and outputs

  - Connect virtually any source to virtually any destination using pre-existing plugins
  - Scalability
    - Write any input, filter, or output plugin in C language
    - WASM: [WASM filter plugins](https://docs.fluentbit.io/manual/development/wasm-filter-plugins) or [WASM input plugins](https://docs.fluentbit.io/manual/development/wasm-input-plugins)
    - 奖励: [Write filters in Lua](https://docs.fluentbit.io/manual/pipeline/filters/lua) or [Write output plugins in Golang](https://docs.fluentbit.io/manual/development/golang-output-plugins)

- [monitoring](https://docs.fluentbit.io/manual/administration/monitoring): Expose internal metrics via HTTP in JSON and [Prometheus](https://prometheus.io/) formats

- [stream processing](https://docs.fluentbit.io/manual/stream-processing/introduction): Perform data selection and transformation using simple SQL queries

  Create new data streams using query results
  - Aggregation windows
  - Data analysis and forecasting: Time series forecasting

- Portable: Runs on Linux, macOS, Windows, and BSD systems

Integrating the new version of Fluent Bit enhances the information collection capability, allowing Fluent Operator to handle more complex data information.

## Project Details

With the rapid development of cloud-native technology and the continuous iteration of technology, higher requirements have been proposed for log collection, processing, and forwarding. The log solution under cloud-native architecture is quite different from the log architecture design based on physical machines or virtual machines. As a graduated project of CNCF, Fluent Bit is undoubtedly one of the preferred solutions for solving the logging problem in the cloud environment. However, installing, deploying, and configuring Fluent Bit in Kubernetes has a certain threshold, which increases the user's usage cost.

On January 21, 2019, the KubeSphere community developed Fluentbit Operator for managing Fluent Bit in a cloud-native way, and released version v0.1.0 on February 17, 2020. Since then, the product has been continuously iterated, and on August 4, 2021, Fluentbit Operator was officially donated to the Fluent community.

Fluentbit Operator reduces the threshold for using Fluent Bit, and efficiently and quickly processes log information. However, the log processing capability of Fluent Bit is slightly weaker, and the log processing tools such as Fluentd has not been integrated, which has more plugins. Based on the above needs, Fluentbit Operator integrated Fluentd and renamed itself as Fluent Operator (GitHub address: https://github.com/fluent/fluent-operator), aiming to integrate Fluentd as an optional log aggregation and forwarding layer. We released the version v1.0.0 of Fluent Operator on March 25, 2022, and version v2.0.0 on February 3, 2023, and will continue to iterate Fluent Operator to add more features and highlights into it.

With Fluent Operator, Fluent Bit and Fluentd can be flexibly and conveniently deployed, configured, and uninstalled. At the same time, the community provides a large number of plugins that support Fluentd and Fluent Bit, by which users can customize the configuration according to their actual situation. The official documentation provides detailed examples that are easy to get started with, greatly reducing the usage threshold for Fluent Bit and Fluentd.

## Outcomes

Complete the integration of Fluent-bit 3.0 into Fluent Operator.
Selectively adapt relevant features of Fluent-bit 3.0 based on requirements and urgency.
Conduct compatibility testing to ensure seamless compatibility.

## Links

- https://github.com/fluent
- https://github.com/fluent/fluent-operator
- https://github.com/kubesphere-sigs/fluent-operator-walkthrough
- https://docs.fluentbit.io/manual/pipeline/inputs

## Quick Start

First, you can [install a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). Then, after KubeSphere starts successfully, you can install Fluent Operator from the [Fluent Operator Helm chart repository](https://github.com/fluent/fluent-operator/tree/master/charts) to experience the log collection function of Fluent Operator.

## Issues for Newbies

- [Fluent-Operator area newbie-friendly issues](https://github.com/fluent/fluent-operator/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22)

## Potential Mentors

- [wenchajun](https://github.com/wenchajun)
- Email: 995729579@qq.com

  