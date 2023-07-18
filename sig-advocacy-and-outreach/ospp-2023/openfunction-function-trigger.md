## Project

OpenFunction function trigger

## Project Goal

Design OpenFunction function trigger patterns to enhance the function trigger experience.

## Skills to Learn/Improve

* Kubernetes
* Dapr
* OpenFunction
* Keda
* Golang、Knative[optional]

## Background

[OpenFunction](https://github.com/OpenFunction/OpenFunction) is a cloud-native open-source Functions-as-a-Service (FaaS) platform designed to allow users to focus on their business logic without worrying about the underlying runtime environment and infrastructure. Users only need to submit business-related source code in the form of functions, and the service can be run on-demand in the cluster.

[Dapr](https://dapr.io/) is a portable, serverless, event-driven runtime that enables developers to easily build resilient, stateless and stateful microservices that run on cloud and edge, and supports multiple languages and development frameworks. 

[Knative](https://knative.dev/) is a Google open-source serverless architecture solution designed to provide a simple and easy-to-use serverless solution that standardizes the serverless paradigm.

## Project Details

Currently, the OpenFunction Function CRD has some complexity in configuration and reconciliation logic, such as the input/output configuration for functions and different configurations for synchronous and asynchronous functions. This proposal aims to simplify the core architecture of OpenFunction, improve users' understanding of the project's value, reduce learning costs, and eliminate the sense of fragmentation in usage.

We will unify the configurations for asynchronous and synchronous functions, and differentiate the implementation logic of underlying functions by adding function triggers and related configurations. REST API triggers will generate synchronous functions as before, while other triggers will generate asynchronous functions as before.

At the same time, we are exploring the use of a synchronous function solution based on the keda-http-addon to unify the core architecture of OpenFunction and improve consistency.

Benefits:

- Eliminating the sense of fragmentation in usage
- Streamlining the core architecture of OpenFunction

Key steps:

- Adjust the configuration of Function CRD
- Verify the possibility of using Keda-http-addon with Dapr to implement synchronous functions
- Complete the adjustments to the OpenFunction architecture (deployment, usage, etc.)

## Outcomes

Potential outcomes may include:

- Adding trigger features to OpenFunction
- Adding a synchronous function engine based on keda-http-addon to OpenFunction (advanced)
- Optimizing the core architecture of OpenFunction (advanced)

## Links

* https://dapr.io/
* https://github.com/OpenFunction/OpenFunction
* https://github.com/kedacore/http-add-on

## Quick Start

You can start by [installing OpenFunction](https://openfunction.dev/docs/getting-started/) and then [creating a simple function](https://openfunction.dev/docs/getting-started/quickstarts/) .

Next, you can learn about [Dapr](https://docs.dapr.io/) and [Keda](https://keda.sh/) projects. It is suitable for beginners to start with [Dapr Quickstarts](https://docs.dapr.io/getting-started/quickstarts/) and [Keda samples](https://github.com/kedacore/samples).

Afterwards, you can learn about the [http-add-on](https://github.com/kedacore/http-add-on) project, which is a scaler provided by Keda for handling synchronous requests.

## Potential Mentors

* [Fang Tian](https://github.com/tpiperatgod/) ，<fangtian@kubesphere.io>