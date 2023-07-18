## Project

Upgrade KubeSphere-S2I with Shipwright and Buildpacks 

## Project Goal

SourceToImage feature based on Shipwright+Buildpacks on KubeSphere.

## Skills to Learn/Improve

- Golang
- Kubernetes
- Buildpacks
- Shipwright 
- React (frontend)

## Background

`Source-to-image (S2I)` is a toolbox and workflow used to directly input source code and package it into a runnable program in a Docker image. It facilitates building images without understanding Dockerfile. By placing the source code into a Builder image working for compiling the source code, S2I automatically packages the compiled code into a Docker image.

`Buildpacks` is a cloud-native container image building technology that supports modern language ecosystems. It shields developers from the details of application building and deployment, such as selecting the operating system, writing scripts to adapt to the image operating system, optimizing image size, and more. It produces OCI container images that can run on any cluster compatible with the OCI image standard.

`Shipwright` is a scalable framework for building container images on Kubernetes, supporting many popular tools for building container images, such as Kaniko, Cloud Native Buildpacks, Buildah, and more.

`KubeSphere-DevOps` is a cloud-native DevOps tool on KubeSphere, which currently integrates Pipeline (based on Jenkins) and continuous deployment (based on Argo CD).

## Project Details

`S2I` is a very early project on KubeSphere that was developed based on `Docker in Docker`. This approach heavily depends on Docker and cannot be used in environments without Docker, which is not elegant and has certain security issues. Although S2I is part of DevOps, it is not displayed in the DevOps tab on the KubeSphere front-end page.

The main goal of this project is to transform S2I based on the latest container image building technology Buildpacks and integrate it into the DevOps tab by unifying it with Shipwright:

- Know well of K8S, Buildpacks, Shipwright, React, S2I/DevOps in KubeSphere, etc.
- Build the basic for multiple programming languages - Buildpacks builders.
- Build new S2I services and installation packages based on Shipwright and Buildpacks.
- Support user-defined Buildpacks builders.
- Transform the KubeSphere console front-end to integrate the S2I service into the DevOps tab.

## Outcomes

- Basic for multiple programming languages - Buildpacks builders
- New S2I service (including front-end) and the helm installation package for the service

## Links
- [Kubesphere-S2I](https://kubesphere.io/zh/docs/v3.3/project-user-guide/image-builder/source-to-image/)
- [Shipwright](https://shipwright.io/docs/)
- [Buildpacks](https://buildpacks.io/docs/)
- [Kubesphere-DevOps](https://github.com/kubesphere/ks-devops)
- [helm](https://helm.sh/)

## Potential Mentors
[yudong](https://github.com/yudong2015)