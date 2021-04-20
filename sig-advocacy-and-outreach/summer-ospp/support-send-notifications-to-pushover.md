# Project

Support Send Notifications To Pushover

## Project Goal

Make the notification manager support send notifications to pushover.

## Skills to Learn/Improve

* Golang
* REST API
* Kubernetes

## Background

Notification Manager manages notifications in multi-tenant K8s environment. It receives alerts or notifications from different senders and then sends notifications to various tenant receivers, such as DingTalk, email, slack, WeCom, webhook, based on alerts/notifications' tenant label like "namespace".

Pushover is a platform for sending and receiving push notifications. On the server-side, it provides an HTTP API for queueing messages to deliver to devices addressable by User or Group Keys. On the device side, the iOS, Android, and Desktop clients receive those push notifications, show them to the user, and store them for offline viewing.

Now we hope to make the notification manager support send notifications to pushover.

## Project details

Pushover uses a simple, versioned REST API to receive messages and broadcast them to devices running our device clients. It is simply for the user registration process and usage of the API, there are no complicated out-of-band authentication mechanisms or per-call signing libraries required, such as OAuth. Standard HTTP libraries available in just about every language, or even from the command line, can be used without any custom modules or extra dependencies needed. 

We can send notifications to pushover through call the API.

## Scope

TODO

## Outcomes

TODO

## Links

- https://github.com/kubesphere/notification-manager
- https://pushover.net/
- https://pushover.net/api

## Quickstart

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/).

## Potential Mentors

- [benjaminhuo](https://github.com/benjaminhuo)
- [lei](https://github.com/wanjunlei)