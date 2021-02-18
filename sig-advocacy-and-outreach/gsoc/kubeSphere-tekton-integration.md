## Project goal

Integrate [Tekton](https://github.com/tektoncd/pipeline) as an alternative CI/CD engine of [KubeSphere](https://github.com/kubesphere/kubesphere/) DevOps.

## Skills to study/improve

* Golang
* Tekton
* Jenkins
* Kubernetes

## Details

### Background

Tekton is a cloud-native CI/CD project. Instead of Jenkins, Tekton can take full advantage of the Kubernetes ecosystem. For example, Tekton is a serverless component, it's very easy to scale. But the hard part is that Tekton is not a friendly product for new users. It does not have a handy UI. We want to the advantage of Tekton, and make it be easy to use in KubeSphere.

### Project details

Currently, Jenkins is the engine of KubeSphere DevOps component. The [Pipeline controller](https://github.com/kubesphere/kubesphere/blob/master/pkg/controller/pipeline/pipeline_controller.go) responsible for converting the CRD of the pipeline to the Jenkins job.
Please consider the compatibility of the [CRD](https://github.com/kubesphere/kubesphere/blob/master/pkg/apis/devops/v1alpha3/pipeline_types.go). Jenkins still needs to be the first choice until we have enough reason to change it.

## Scope

Consider GSoC 2021 only has one phase, you can just finish the backend part. It means that using the CLI to achieve our goal is accepted. For example, users can use [kubectl](https://github.com/kubernetes/kubectl) to create, trigger, view the log of Pipelines.

## Outcome

The potential outcome might include:
* Pipeline CRD compatible with Jenkins
* Log, the archive storage solution
* Multi-branch Pipeline support
* A how-to document that contains the integration, usage, users case

## Links

* http://jenkins.io/
* https://github.com/jenkins-x
* https://github.com/kubesphere

## Quick-start

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). [Enable the DevOps](https://kubesphere.io/docs/pluggable-components/devops/) component once KubeSphere is ready. Then explore KubeSphere by yourself.
[Installing Tekton Pipelines](https://github.com/tektoncd/pipeline/blob/master/docs/install.md) first, then Jump in with [the tutorial](https://github.com/tektoncd/pipeline/blob/master/docs/tutorial.md)!

## Newbie-friendly issues
* [DevOps area newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+label%3A%22area%2Fdevops%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)

## Potential Mentors

* [Rick](https://github.com/LinuxSuRen/)
* [Shaowen Chen](https://github.com/shaowenchen/)
