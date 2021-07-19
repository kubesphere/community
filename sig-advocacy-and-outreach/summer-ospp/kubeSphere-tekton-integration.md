# Project

KubeSphere Tekton Integration

## Project Goal

Integrate [Tekton](https://github.com/tektoncd/pipeline) as an alternative CI/CD engine of [KubeSphere](https://github.com/kubesphere/kubesphere/) DevOps.

## Skills to Learn/Improve

* Golang
* Kubernetes
* Tekton
* JavaScript[Optional]
* Jenkins[Optional]

## Background

Tekton is a cloud-native CI/CD project. Compared to Jenkins, Tekton can take full advantage of the Kubernetes ecosystem. For example, Tekton, as a serverless component, is very easy to scale. However, it could be difficult for new users to operate Tekton for its lack of user-friendly UI. We would like to make full use of the advantages of Tekton, and make it easy to use in KubeSphere.

## Project details

Currently, Jenkins is the engine of KubeSphere DevOps component. The [Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) is responsible for converting the CRD of pipelines to Jenkins jobs.
Please consider the compatibility of [CRD](https://github.com/kubesphere/kubesphere/blob/master/staging/src/kubesphere.io/api/devops/v1alpha3/pipeline_types.go). Whenever possible, Jenkins and Tekton share a CRD.

## Scope

You can start with Tekton deployment, then complete the management of Trigger, Task, and Pipeline, followed by graphical editing, running, and viewing. In the graphical phase, try to consider CRD compatibility.

## Outcomes

The potential outcomes might include:
* Solution for Tekton deployment in KubeSphere
* Tekton integration under multi-tenancy, including frontend and backend
* Log, and the archive storage solution
* A how-to document that contains the integration, usage, users case
* Pipeline CRD compatible with Jenkins

## Links

* https://tekton.dev/
* http://jenkins.io/
* https://github.com/kubesphere/kubesphere

## Quickstart

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Enable the DevOps](https://kubesphere.io/docs/pluggable-components/devops/) component once KubeSphere is ready and explore KubeSphere DevOps system by yourself.
[Install Tekton Pipelines](https://github.com/tektoncd/pipeline/blob/master/docs/install.md) first, then get familiar with various features by following [the tutorial](https://github.com/tektoncd/pipeline/blob/master/docs/tutorial.md)!

## Newbie-Friendly Issues

* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)

## Potential Mentors

* [Shaowen Chen](https://github.com/shaowenchen/)
* [Rick](https://github.com/LinuxSuRen/)
