## Project goal

Split the Jenkins client from [KubeSphere](https://github.com/kubesphere/kubesphere/). Or use an existing Jenkins client.

## Skills to study/improve

* Golang
* REST API
* OpenAPI
* Jenkins
* Kubernetes

## Details

### Background

Currently, KubeSphere communicates to Jenkins with XML API instead of REST API. The drawback of using XML API is that it needs to deal with the details of Jenkins or Jenkins plugins implement. That means any changes from Jenkins or Jenkins plugins might lead the API to be unstable. Perhaps version number changes also could make it be unstable too. Considering the REST API is a much stable way to communicate to Jenkins. 

### Project details

[Jenkins](https://github.com/jenkinsci/jenkins) is the leading open-source automation server. Built with Java, it provides over 1,700 plugins to support automating virtually anything. Jenkins is the engine of KubeSphere DevOps component. The [Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) responsible for converting the CRD of the pipeline to the Jenkins job.
You can find the code base of Jenkins client from [pkg/simple/client/devops](https://github.com/kubesphere/kubesphere/tree/master/pkg/simple/client/devops).

## Links

* http://jenkins.io/
* https://github.com/kubesphere
* https://github.com/jenkins-zh/jenkins-cli
* [Tutorial from Jenkins community](https://www.jenkins.io/doc/tutorials/)
* [Jenkins Remote Access API](https://www.jenkins.io/doc/book/using/remote-access-api/)

## Quick-start

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Enable the DevOps](https://kubesphere.io/docs/pluggable-components/devops/) component once KubeSphere is ready.

## Newbie-friendly issues

* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## Potential Mentors

* [Rick](https://github.com/LinuxSuRen/)
* [Shaowen Chen](https://github.com/shaowenchen/)
