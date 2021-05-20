# Project

OpenFunction's nodejs function framework development

## Project Goal

Develop a functional framework for working with nodejs code, providing users with a suite of tools for their code in a cloud-native environment.

开发用于处理 nodejs 代码的函数框架，为用户的业务代码提供适用于云原生环境的多种工具套件。

## Skills to Learn/Improve

* Nodejs
* Kubernetes
* CloudEvent
* Dapr
* OpenFunction
* Cloud Native Buildpacks
* Golang、Knative[可选]

## Background

[OpenFunction](https://github.com/OpenFunction/OpenFunction) is a cloud-native open source FaaS (Function as a Service) platform aiming to enable users to focus on their business logic without worrying about the underlying runtime environment and infrastructure. Users only need to submit business-related source code in the form of functions.

[Dapr](https://dapr.io/) is a portable, serverless, event-driven runtime that makes it easy for developers to build elastic, stateless and stateful microservices that run on the cloud and the edge, and include multiple languages and development frameworks.

[Knative](https://knative.dev/) is Google's open source serverless architecture solution, which aims to provide an easy-to-use serverless solution to standardize serverless.

## Project details

In the current serverless framework, event sources will drive the serverless to spawn workloads. It recommeds that user applications should support multiple driver sources such as HTTP, CloudEvent, Dapr bindings, etc. To reduce the cost of developing applications for users, OpenFunction needs to provide a tool suite for user functions to adapt to the serverless ecosystem.

Development of function conversion suites for different programming languages.

- Main function template

  During the build process of OpenFunction, the builder passes relevant crd resource properties and environment variables into the Main function template, which is rendered to produce the code in the final application.

- Function tool suite

  Used to provide user functions with a suite of tools adapted to the serverless ecosystem, such as support for HTTP, CloudEvent, Dapr bindings, and other drivers.

Currently our function builder uses [GoogleCloudPlatform's functions-framework](https://github.com/GoogleCloudPlatform/functions-framework). This functions-framework does not support drivers other than HTTP and CloudEvent.

We want to:

1. Provide a nodejs function framework that can be adapted to HTTP, CloudEvent, Dapr bindings.

## Scope

You can start with OpenFunction and then use OpenFunction/builder to build your function and run it successfully.

## Outcomes

The potential outcomes might include:

* Complete the development of a function framework that can handle nodejs code
* Write test cases, usage notes for nodejs function framework
* Develop function frameworks for other languages if you are interested
* Produce your knowledge and understanding of OpenFunction, functions-framework

## Links

* https://github.com/GoogleCloudPlatform/functions-framework
* https://dapr.io/
* https://github.com/OpenFunction/OpenFunction
* https://buildpacks.io/

## Quickstart

You can start with [install OpenFunction](https://github.com/OpenFunction/OpenFunction#install) and [create a simple function](https://github.com/OpenFunction/OpenFunction#quickstart) .  You can refer to [gcp's functions-framework](https://github.com/GoogleCloudPlatform/functions-framework) to learn about the principles of functions frameworks.

## Newbie-Friendly Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)
* [Tekton good-first-issues](https://github.com/tektoncd/pipeline/labels/good%20first%20issue)

## Potential Mentors

* [Benjamin Huo](https://github.com/benjaminhuo)

* [Fang Tian](https://github.com/tpiperatgod/), <fangtian@yunify.com>
