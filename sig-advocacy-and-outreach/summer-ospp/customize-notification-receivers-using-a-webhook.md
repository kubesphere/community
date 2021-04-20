https://hackmd.io/@kA_hXb92SEWvsiZemHcP5Q/SkkgNJfL_/edit

## Project Goal

Enable [Notification Manager](https://github.com/kubesphere/notification-manager) to obtain a notification receiver list from a webhook so that users can customize the notification receivers.

## Skills to Learn/Improve

* Golang
* REST API
* Kubernetes

## Background

Currently, Notification Manager determines the notification receivers based on the RoleBindings of a namespace. Under this mechanism, certain users who need to receive notifications may not be notified. For example, when a user has the authority to manage a namespace but is not in the namespace, notifications from the namespace are not sent to the user.

We hope to provide a mechanism that allows users to customize the notification receivers.

## Project details

We plan to inject a sidecar into the Notification Manager deployment, which implements the logic of obtaining the receiver list. The sidecar needs to support the following features:

* Provides an interface for obtaining the receiver list based on the namespace. The interface should have uniform input parameters and return values.
* Caches the receiver list to reduce resource consumption.

## Scope

TODO

## Outcomes

TODO

## Links

* https://github.com/kubesphere/notification-manager
* https://kubesphere.com.cn/en/docs/cluster-administration/cluster-wide-alerting-and-notification/notification-manager/

## Quickstart

You can start with a [minimal KubeSphere system](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). 

## Potential Mentors

* [Benjamin Huo](https://github.com/benjaminhuo)
* [Wanjun Lei](https://github.com/wanjunlei)
