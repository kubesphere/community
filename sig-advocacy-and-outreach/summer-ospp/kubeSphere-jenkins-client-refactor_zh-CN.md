https://hackmd.io/@kA_hXb92SEWvsiZemHcP5Q/ryoPXyzUd/edit

## 项目目标

Split the Jenkins client from [KubeSphere](https://github.com/kubesphere/kubesphere/). Or use an existing Jenkins client.

## 技术要求

* Golang
* REST API
* OpenAPI
* Jenkins
* Kubernetes

## 项目背景

Currently, KubeSphere communicates to Jenkins with the XML API instead of the REST API. The drawback of using the XML API is that it needs to deal with the details related to Jenkins or Jenkins plugins implementation. It means that any changes from Jenkins or Jenkins plugins might cause instability in the API. Moreover, version number changes might also cause instability in the API. By comparison, the REST API is a stabler way to communicate to Jenkins. 

## 项目详情

[Jenkins](https://github.com/jenkinsci/jenkins) is the leading open-source automation server. Built with Java, it provides over 1,700 plugins to support automating virtually anything. Jenkins is the engine of KubeSphere DevOps component. The [Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) is responsible for converting the CRD of pipelines to Jenkins jobs.
You can find the code base of Jenkins client from [pkg/simple/client/devops](https://github.com/kubesphere/kubesphere/tree/master/pkg/simple/client/devops).

## 项目范围

TODO

## 项目产出

TODO

## 链接

* http://jenkins.io/
* https://github.com/kubesphere
* https://github.com/jenkins-zh/jenkins-cli
* [Tutorial from Jenkins community](https://www.jenkins.io/doc/tutorials/)
* [Jenkins Remote Access API](https://www.jenkins.io/doc/book/using/remote-access-api/)

## 快速入门

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Enable the DevOps](https://kubesphere.io/docs/pluggable-components/devops/) component once KubeSphere is ready.

## 入门 Issues

* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## 导师/联系方式

* [Rick](https://github.com/LinuxSuRen/)
* [Shaowen Chen](https://github.com/shaowenchen/)

