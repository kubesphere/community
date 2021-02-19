## Project goal

Make the notification manager support to get a user list that will receive the notifications from a webhook.

## Skills to study/improve

* Golang
* REST API
* Kubernetes

## Details

### Background

Currently, the logic for obtaining the user list that will receive the notifications is to obtain the rolebindings according to ns, then obtain the user list through the rolebindings. This method cannot handle some special situations, for example, the user is not in this ns, but has the authority to manage this ns, in this case, the user should be notified. So we hope to provide a mechanism that allows users to determine which users can receive alerts from a webhook.

### Project details

We hope to inject a sidecar into notification manager deployment, and this sidecar will implement the logic of obtaining the user list. This sidecar needs to implement the following functions.

* Provide an interface to obtain a list of users who need to receive notifications according to the namespace. This interface should have uniform input parameters and return values.
* Cache the user list to reduce resource consumption.

## Links

* https://github.com/kubesphere/notification-manager
* https://kubesphere.com.cn/en/docs/cluster-administration/cluster-wide-alerting-and-notification/notification-manager/

## Quick-start

You can start with a [minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). 

## Potential Mentors

* [benjaminhuo](https://github.com/benjaminhuo)
* [lei](https://github.com/wanjunlei)
