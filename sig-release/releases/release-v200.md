---
title: "Release Notes For 2.0.0"
keywords: "kubernetes, docker, kubesphere, jenkins, istio, prometheus"
description: "KubeSphere Release Notes For 2.0.0"
---

KubeSphere 2.0.0 was released on **May 18th, 2019**. 

## What's New in 2.0.0

### Component Upgrades

- Support Kubernetes [Kubernetes 1.13.5](https://github.com/kubernetes/kubernetes/releases/tag/v1.13.5)
- Integrate [QingCloud Cloud Controller](https://github.com/yunify/qingcloud-cloud-controller-manager). After installing load balancer, QingCloud load balancer can be created through KubeSphere console and the backend workload is bound automatically.  
- Integrate [QingStor CSI v0.3.0](https://github.com/yunify/qingstor-csi/tree/v0.3.0) storage plugin and support physical NeonSAN storage system. Support SAN storage service with high availability and high performance.
- Integrate [QingCloud CSI v0.2.1](https://github.com/yunify/qingcloud-csi/tree/v0.2.1) storage plugin and support many types of volume to create QingCloud block services.
- Harbor is upgraded to 1.7.5.
- GitLab is upgraded to 11.8.1.
- Prometheus is upgraded to 2.5.0.

### Microservice Governance

- Integrate Istio 1.1.1 and support visualization of service mesh management.
- Enable the access to the project's external websites and the application traffic governance.
- Provide built-in sample microservice [Bookinfo Application](https://istio.io/docs/examples/bookinfo/).
- Support traffic governance.
- Support traffic images.
- Provide load balancing of microservice based on Istio.
- Support canary release.
- Enable blue-green deployment.
- Enable circuit breaking.
- Enable microservice tracing.

### DevOps (CI/CD Pipeline)

- CI/CD pipeline provides email notification and supports the email notification during construction.
- Enhance CI/CD graphical editing pipelines, and more pipelines for common plugins and execution conditions.
- Provide source code vulnerability scanning based on SonarQube 7.4.
- Support [Source to Image](https://github.com/kubesphere/s2ioperator) feature.

### Monitoring

- Provide Kubernetes component independent monitoring page including etcd, kube-apiserver and kube-scheduler.
- Optimize several monitoring algorithm.
- Optimize monitoring resources. Reduce Prometheus storage and the disk usage up to 80%.

### Logging

- Provide unified log console in terms of tenant.
- Enable accurate and fuzzy retrieval.
- Support real-time and history logs.
- Support combined log query based on namespace, workload, Pod, container, key words and time limit.  
- Support detail page of single and direct logs. Pods and containers can be switched.
- [FluentBit Operator](https://github.com/kubesphere/fluentbit-operator) supports logging gathering settings: ElasticSearch, Kafka and Fluentd can be added, activated or turned off as log collectors. Before sending to log collectors, you can configure filtering conditions for needed logs.

### Alerting and Notifications

- Email notifications are available for cluster nodes and workload resources. 
- Notification rules: combined multiple monitoring resources are available. Different warning levels, detection cycle, push times and threshold can be configured.
- Time and notifiers can be set.
- Enable notification repeating rules for different levels.

### Security Enhancement

- Fix RunC Container Escape Vulnerability [Runc container breakout](https://log.qingcloud.com/archives/5127)
- Fix Alpine Docker's image Vulnerability [Alpine container shadow breakout](https://www.alpinelinux.org/posts/Docker-image-vulnerability-CVE-2019-5021.html)
- Support single and multi-login configuration items.
- Verification code is required after multiple invalid logins.
- Enhance passwords' policy and prevent weak passwords.
- Others security enhancements.

### Interface Optimization

- Optimize multiple user experience of console, such as the switch between DevOps project and other projects.
- Optimize many Chinese-English webpages.

### Others

- Support Etcd backup and recovery.
- Support regular cleanup of the docker's image.

## Bugs Fixes

- Fix delay updates of the resource and deleted pages.
- Fix the left dirty data after deleting the HPA workload.
- Fix incorrect Job status display.
- Correct resource quota, Pod usage and storage metrics algorithm.
- Adjust CPU usage percentages.
- many more bugfix
