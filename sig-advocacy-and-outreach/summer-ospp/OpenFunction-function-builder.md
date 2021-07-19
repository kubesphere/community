# Project

OpenFunction's function builder development.

## Project Goal

Develop and optimize function builder to detect Nodejs, Java, PHP or Rust (optional) programs and package functions into application images that can be run in OpenFunction.

## Skills to Learn/Improve

* Golang
* Kubernetes
* Tekton
* Cloud Native Buildpacks
* OpenFunction
* Python、Nodejs、Java、PHP、Rust[All optional]

## Background

[OpenFunction](https://github.com/OpenFunction/OpenFunction) is a cloud-native open source FaaS (Function as a Service) platform aiming to enable users to focus on their business logic without worrying about the underlying runtime environment and infrastructure. Users only need to submit business-related source code in the form of functions.

[Tekton](https://github.com/tektoncd) is a cloud-native CI/CD project.

[Cloud Native Buildpacks](https://github.com/buildpacks) is a cloud-native OCI format image creation tool. (hereinafter referred to as Buildpacks)

## Project details

OpenFunction's builders crd integrates Tekton and Buildpacks to do the part of making user submitted function code into application images that can run in Kubernetes.

Tekton is responsible for orchestrating the process from code to application image, including several major steps: *pulling images*, *preparing environment variables*, *build images with Buildpacks*, and *exporting images to repository*.

Buildpacks is responsible for detecting the program language of the code, then preparing the relevant compilation environment, and then rendering the code into a runnable application via function framework templates.

Schematic diagram of the builder:

![build diagram](https://buildpacks.io/docs/concepts/operations/build.svg)

The builder project is: [OpenFunction/builder](https://github.com/OpenFunction/builder) . And the current status refer to: [Status](https://github.com/OpenFunction/builder#status).

We want that.

1. The builder can support more mainstream languages (and more versions)
2. The builder can optimize the strategy of code building while reduce the time.

## Scope

You can start with OpenFunction and then use OpenFunction/builder to build your function and run it successfully.

## Outcomes

The potential outcomes might include:

* Complete development of new builders, including but not limited to: 1. PHP language builder; 2. Rust language builder.
* Optimization of current builders, including but not limited to: 1. providing additional version support; 2. builder strategy optimization.
* Writing test cases, usage notes for the new builders
* Produce your knowledge and understanding of OpenFunction, Tekton, Buildpacks

## Links

* https://tekton.dev/
* https://buildpacks.io/
* https://github.com/OpenFunction/OpenFunction
* https://github.com/OpenFunction/builder

## Quickstart

You can start with [install OpenFunction](https://github.com/OpenFunction/OpenFunction#install) and [create a simple function](https://github.com/OpenFunction/OpenFunction#quickstart) . Then try to build your own function builder, refer to [go1.15](https://github.com/OpenFunction/builder/tree/main/builders/go115#build-builder-of-go-version-115) .

## Newbie-Friendly Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/labels/good%20first%20issue)

## Potential Mentors

* [Benjamin Huo](https://github.com/benjaminhuo)

* [Fang Tian](https://github.com/tpiperatgod/), <fangtian@yunify.com>
