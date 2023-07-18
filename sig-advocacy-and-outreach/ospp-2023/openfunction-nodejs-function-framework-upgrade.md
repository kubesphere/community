## Project

The Node.js functions framework of OpenFunction supports Dapr state management

## Project Goal

Upgrade the existing OpenFunction Node.js Functions Framework to support using Dapr state management in functions.

## Skills to Learn/Improve

- Node.js
- Kubernetes
- KinD
- OpenFunction
- Dapr

## Background

[OpenFunction](https://github.com/OpenFunction/OpenFunction) is a cloud-native open-source Functions-as-a-Service (FaaS) platform designed to allow users to focus on their business logic without worrying about the underlying runtime environment and infrastructure. Users only need to submit business-related source code in the form of functions, and the service can be run on-demand in the cluster.

[Dapr](https://dapr.io/) is a portable, cross-platform, event-driven runtime that enables developers to easily build resilient, stateless and stateful microservices that run on cloud and edge, and supports multiple languages and development frameworks. OpenFunction integrates Dapr as a technical pivot for the asynchronous output of both asynchronous and synchronous functions.

[KinD](https://kind.sigs.k8s.io/) is a tool for running Kubernetes clusters on local machines, using Docker containers as nodes to run Kubernetes control plane and workloads. With KinD, it's quick and easy to create Kubernetes clusters for testing and development, both locally and in CI/CD environments.

## Project Details

Currently, OpenFunction supports Dapr [Pub/Sub](https://docs.dapr.io/reference/components-reference/supported-pubsub/) and [Bindings](https://docs.dapr.io/reference/components-reference/supported-bindings/) building blocks, and [State Management](https://docs.dapr.io/reference/components-reference/supported-state-stores/) is another useful building block for stateful functions. With state store components, stateful, long-running functions can be built to persist and retrieve their state.

The latest infrastructure service of OpenFunction has [already supported](https://github.com/OpenFunction/OpenFunction/pull/427) state management capability, and we expect to enable [this feature](https://github.com/OpenFunction/OpenFunction/pull/426) for Node.js functions in this project.

In addition, we expect you to refer to the [Go Functions Framework](https://github.com/OpenFunction/functions-framework-go) to implement end-to-end automated testing based on KinD, to further enhance the functionality and robustness of the Node.js functions framework.

## Outcomes

Potential outcomes may include:

- Adding support for state management capability to the Node.js functions framework
- Writing corresponding test cases, sample functions, and usage instructions for the added state management feature
- Adding an end-to-end testing framework and test cases based on KinD to the Node.js Functions Framework project

## Quick Start

You can quickly learn about the basic capabilities of OpenFunction and the Node.js functions framework by reading [OpenFunction Talks](https://github.com/webup/openfunction-talks).

You can also get hands-on experiences by [installing OpenFunction](https://github.com/OpenFunction/OpenFunction#install) and then [creating a simple function](https://github.com/OpenFunction/OpenFunction#quickstart); and refer to [OpenFunction Node.js Functions Framework](https://github.com/OpenFunction/functions-framework-nodejs) to learn about the current features and specific implementations of the Node.js functions framework.

## Potential Mentors

- [Haili Zhang](https://github.com/webup)