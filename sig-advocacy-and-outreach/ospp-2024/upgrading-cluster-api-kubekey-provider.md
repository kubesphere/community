
# Project

Upgrading cluster-api-kubekey-provider

## Project Goal

Upgrading cluster-api-kubekey-provider using a framework and task separation architecture.

## Skills to Learn/Improve

- Backend languages: Golang, Shell
- Workflow syntax: Ansible, Pongo2
- Kubernetes cluster: Kubernetes, Helm, cluster-api, autoscaler

## Background

KubeKey has already been integrated into cluster-api (cluster-api-kubekey-provider). However, due to the diversity and richness of Kubernetes cluster components, the current coverage of KubeKey for the complete set of cluster components has made the KubeKey project increasingly large. Therefore, a framework and task separation approach is adopted to decouple the management tasks of Kubernetes. Accordingly, the cluster-api-kubekey-provider also needs to be upgraded.

## Project Details

The core framework is developed using Golang. The core package aims to be small and concise. It supports both command-line mode and CRD (Custom Resource Definition) mode for driving.

Task templates are written in YAML format. Tasks can be stored locally or in a remote Git repository. Tasks can be infinitely extended.

## Development content

In the core framework, we will implement the interface for cluster-api, integrating the standardized API of cluster-api and using it to drive the execution of task templates. We will also implement automatic scaling for the autoscaler.

In the task templates, we will design task flows that meet the requirements of the KubeKey framework, allowing for the management of Kubernetes clusters, including adding and deleting nodes.

## Outcomes

- Develop a cluster lifecycle management controller for KubeKey based on the framework and task separation architecture, following the cluster-api standards.
- Provide operational guides and documentation as output.

## Potential Mentors

- [Liu Jian](https://github.com/ImitationImmortal)
- Email: blacktiledhouse@gmail.com