## Project

Development of the Fluent Operator Collector input component

## Project Goal

Complete the development of multiple input plugins of [Fluent Operator](https://github.com/fluent/fluent-operator) and integrate them into Fluent Operator.

## Skills to Learn/Improve

- Golang
- Kubernetes
- Fluent-bit
- Fluentd

## Background

Fluent Operator supports many plugins of Fluentd and Fluent Bit. Seven input components of Fluent Bit have been integrated into Fluent Operator. As Fluent Bit has strong extensibility and many plugins, there are still many plugins that have not been integrated into Fluent Operator, which include the following input plugins (for reference: https://github.com/fluent/fluent-operator/issues/304#issuecomment-1338661126)：

- https://docs.fluentbit.io/manual/pipeline/inputs/opentelemetry
- https://docs.fluentbit.io/manual/pipeline/inputs/collectd
- https://docs.fluentbit.io/manual/pipeline/inputs/forward
- https://docs.fluentbit.io/manual/pipeline/inputs/http
- https://docs.fluentbit.io/manual/pipeline/inputs/mqtt
- https://docs.fluentbit.io/manual/pipeline/inputs/nginx
- https://docs.fluentbit.io/manual/pipeline/inputs/statsd
- https://docs.fluentbit.io/manual/pipeline/inputs/syslog
- https://docs.fluentbit.io/manual/pipeline/inputs/tcp

Adding various input plugins helps enhance the information collection capabilities of Fluent Bit, and strengthens the capabilities of Fluent Operator to handle more complex data.

## Project Details

With the rapid development of cloud-native technology and the continuous iteration of technology, higher requirements have been proposed for log collection, processing, and forwarding. The log solution under cloud-native architecture is quite different from the log architecture design based on physical machines or virtual machines. As a graduated project of CNCF, Fluent Bit is undoubtedly one of the preferred solutions for solving the logging problem in the cloud environment. However, installing, deploying, and configuring Fluent Bit in Kubernetes has a certain threshold, which increases the user's usage cost.

On January 21, 2019, the KubeSphere community developed Fluentbit Operator for managing Fluent Bit in a cloud-native way, and released version v0.1.0 on February 17, 2020. Since then, the product has been continuously iterated, and on August 4, 2021, Fluentbit Operator was officially donated to the Fluent community.

Fluentbit Operator reduces the threshold for using Fluent Bit, and efficiently and quickly processes log information. However, the log processing capability of Fluent Bit is slightly weaker, and the log processing tools such as Fluentd has not been integrated, which has more plugins. Based on the above needs, Fluentbit Operator integrated Fluentd and renamed itself as Fluent Operator (GitHub address: https://github.com/fluent/fluent-operator), aiming to integrate Fluentd as an optional log aggregation and forwarding layer. We released the version v1.0.0 of Fluent Operator on March 25, 2022, and version v2.0.0 on February 3, 2023, and will continue to iterate Fluent Operator to add more features and highlights into it.

With Fluent Operator, Fluent Bit and Fluentd can be flexibly and conveniently deployed, configured, and uninstalled. At the same time, the community provides a large number of plugins that support Fluentd and Fluent Bit, by which users can customize the configuration according to their actual situation. The official documentation provides detailed examples that are easy to get started with, greatly reducing the usage threshold for Fluent Bit and Fluentd.

## Outcomes

- Complete the development of multiple input components for Fluent Operator
- Complete compatibility testing

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