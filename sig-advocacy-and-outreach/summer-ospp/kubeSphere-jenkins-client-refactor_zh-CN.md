# 项目

KubeSphere Jenkins 客户端重构

## 项目目标

从 [KubeSphere](https://github.com/kubesphere/kubesphere/) 核心代码中的 DevOps 部分将 Jenkins 客户端代码分离开，或者，使用已有的 Jenkins 客户端。

## 技术要求

* Golang
* REST API
* OpenAPI
* Jenkins
* Kubernetes

## 项目背景

在 KubeSphere 中，目前是通过调用 XML 格式的 API 与 Jenkins 进行通讯，而不是更加流行的 RESTful 风格的 API.由于 XML API 的原理是，通过 Java 语言对类对象的反射机制获取、操作数据，因此，非常明显的缺点就是这种 API 的请求数据和 Jenkins 功能的具体实现细节耦合严重。这就意味着 Jenkins 及其插件的更新非常容易导致出现兼容性的问题，甚至只是新安装一个插件都有可能导致无法使用。相比较而言，REST API 则会更加稳定、不容易出问题。

## 项目详情

[Jenkins](https://github.com/jenkinsci/jenkins) 是一个具有丰富的插件生态的开源自动化服务。基于 Java 实现，并提供了超过 1,700 插件，几乎可以实现各种方面的自动化。Jenkins 是 KubeSphere DevOps 组件的核心引擎。[Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) 负责把流水线的 CRD 资源转换并同步为 Jenkins 的任务。

你可以从这里 [pkg/simple/client/devops](https://github.com/kubesphere/kubesphere/tree/master/pkg/simple/client/devops) 找到 Jenkins 客户端部分的代码。

## 项目产出

* 完成 Jenkins 客户端的重构、替换
* 完成兼容性测试

## 链接

* http://jenkins.io/
* https://github.com/kubesphere
* https://github.com/jenkins-zh/jenkins-cli
* [Tutorial from Jenkins community](https://www.jenkins.io/doc/tutorials/)
* [Jenkins Remote Access API](https://www.jenkins.io/doc/book/using/remote-access-api/)

## 快速入门

首先，你可以从安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。然后，当 KubeSphere 启动成功后可以[启用 DevOps](https://kubesphere.io/docs/pluggable-components/devops/) 组件，体验 DevOps 的流水线功能。

## 入门 Issues

* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## 导师/联系方式

* [Rick](https://github.com/LinuxSuRen/)
* [Shaowen Chen](https://github.com/shaowenchen/)

