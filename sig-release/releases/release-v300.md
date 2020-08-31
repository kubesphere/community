---
title: "Release Notes For 3.0.0"
keywords: "kubernetes, docker, kubesphere, jenkins, istio, prometheus"
description: "KubeSphere Release Notes For 3.0.0"
---

## How to get v3.0.0

- [Install KubeSphere v3.0.0 on Linux](https://github.com/kubesphere/kubekey)
- [Install KubeSphere v3.0.0 on existing Kubernetes](https://github.com/kubesphere/ks-installer)

## Release Notes

## **Installer**

### FEATURE

- A brand new installer: [KubeKey](https://github.com/kubesphere/kubekey), v1.0.0, which is turnkey solution to install Kubernetes with KubeSphere in different platform, are more easy to use and reduce the dependency on OS environment 

### UPGRADE & ENHANCEMENT
- Be compatible with Kubernetes 1.15.x, 1.16.x, 1.17.x and 1.18.x for [ks-installer](https://github.com/kubesphere/ks-installer), v3.0.0
- [KubeKey](https://github.com/kubesphere/kubekey) offcially support Kubernetes 1.15.12, 1.16.13, 1.17.9 and 1.18.6(Notice, please avoid using KubeKey to install Kubernetes 1.15 to 1.15.5 and 1.16 to 1.16.2, because Kubernetes has an [API validation issue](https://github.com/kubernetes/kubernetes/issues/83778))
- Add support of EulerOS, UOS and KylinOS
- Add support of Kunpeng and Phytium CPU
- Use ClusterConfiguration to store ks-installer's configuration instead of ConfigMap

## **Cluster Management**

### FEATURE

- Support multiple Kubernetes clusters management
- Support Federated Deployment across multiple clusters

## **Observability**

### FEATURE

- Support custom monitoring for 3rd-party application metrics in KubeSphere console
- Add K8s & KubeSphere auditing support including audit event archiving, searching and alerting
- Add K8s event management support including K8s event archiving, searching and alerting by [kube-events](https://github.com/kubesphere/kube-events)
- Add tenant control to audit/K8s events searching, a tenant user can only search his own audit/K8s events
- Support archiving audit/K8s events to Elasticsearch, Kafka or Fluentd
- Add multi-tenant notification support by [Notification Manager](https://github.com/kubesphere/notification-manager)
- Support Alertmanager v0.21.0

### UPGRADE & ENHANCEMENT

- Upgrade Prometheus Operator to v0.38.3 ( KubeSphere customized version )
- Upgrade Prometheus to v2.20.1
- Upgrade Node Exporter to v0.18.1
- Upgrade kube-state-metrics to v1.9.6
- Upgrade metrics server to v0.3.7
- metrics-server is enabled by default ( Disabled if installing KubeSphere on existing K8s )
- Upgrade Fluent Bit Operator to v0.2.0
- Upgrade Fluent Bit to v1.4.6
- Significantly improve log searching performance
- Allow platform admins to view pod logs from deleted namespaces
- Adjust the display style of log searching results in Toolbox
- Optimize log collection configuration for log files on pod's volume

### BUG FIXES

- Fix time skew in metric graphs for newly created namespaces (#[2868](https://github.com/kubesphere/kubesphere/issues/2868))
- Fix workload-level alerting is not working as expected (#[2834](https://github.com/kubesphere/kubesphere/issues/2834))
- Fix no metric data for NotReady nodes

## **DevOps**

### FEATURE

- Refactor DevOps framework, use CRDs to manage DevOps resources

### UPGRADE & ENHANCEMENT

- Remove Sonarqube from installer default packages, support for external Sonarqube

### BUG FIXES

- Fix the issue that DevOps permissions data is missing in a very limited number of cases 

- Fix the issue that the Button in the Stage page doesn't work (#[449](https://github.com/kubesphere/console/issues/449))
- Fix the issue that the parameterized pipeline fail to send the parameter's value (#[2699](https://github.com/kubesphere/kubesphere/issues/2699))

## **App Store**

### FEATURE

- Support Helm V3
- Support to deploy application templates into multi-cluster
- Support application template upgrade
- Users can view events that occurred during repository synchronization

### UPGRADE & ENHANCEMENT

- Users can use the same application repository name
- Support the application template which contains CRDs
- Merge all OpenPitrix services into one service
- Support HTTP basic authentication when adding the application repository 
- Add and upgrade below apps in App Store:
  AWS EBS CSI Driver 0.5.0 - Helm 0.3.0  
  AWS EFS CSI Driver 0.3.0 - Helm 0.1.0  
  AWS FSX CSI Driver 0.1.0 - Helm 0.1.0  
  Elasticsearch Exporter 1.1.0 - Helm 3.3.0  
  etcd 3.3.12 - Helm 0.1.1  
  Harbor 2.0.0 - Helm 1.4.0  
  Memcached 1.5.20 - Helm 3.2.3  
  Minio master - Helm 5.0.26  
  MongoDB 4.2.1 - Helm 0.3.0  
  MySQL 5.7.30 - Helm 1.6.6  
  MySQL Exporter 0.11.0 - Helm 0.5.3  
  Nginx 1.18.0 - Helm 1.3.2  
  Porter 0.3-alpha - Helm 0.1.3  
  PostgreSQL 12.0 - Helm 0.3.2  
  RabbitMQ 3.8.1 - Helm 0.3.0  
  Redis 5.0.5 - Helm 0.3.2  
  Redis Exporter 1.3.4 - Helm 3.4.1  
  Tomcat 8.5.41 - Helm 0.4.1+1  

### BUG FIXES

- Fix the issue of insufficient length of attachment IDs

## **Network**

### FEATURE

- Support project network isolation by adding controllers to manage custom project network policies
- Support workspace network isolation
- Support to add, view, modify and delete native K8s network policies

## **Service Mesh**

### FEATURE

- Support to clean Jaeger ES Indexer

### UPGRADE & ENHANCEMENT

- Upgrade Istio to v1.4.8

## **Storage**

### FEATURE

- Support volume snapshot management
- Support storage capability
- Support volume monitoring

## **Security**

### FEATURE

- Support LDAP and OAuth login
- Support custom workspace role
- Support custom DevOps project role
- Support  access control across multiple clusters
- Support pod security context(#[1453](https://github.com/kubesphere/kubesphere/issues/1453))

### UPGRADE & ENHANCEMENT

- Simplify the role definition
- Optimize built-in roles

### BUG FIXES

- Fix the issue of login failure due to node clock skew

## **Globalization**

### FEATURE

- Add new languages support, including Spanish, Traditional Chinese

## **User Experience**

### FEATURE
- Support the history record in Toolbox, the user could re-visit the Clusters/Workspaces/Projects/DevOps Projects recently visited, which could also be lanched by shortcut keys

### UPGRADE & ENHANCEMENT

- Refactor global navigation
- Refactor breadcrumbs in detail pages
- Refactor data watching in the resources list
- Simplify project creation
- Refactor composing application creation, and support creating a composing application by YAML
- Add workload revision compare by YAML
- Optimize the display of log query results
- Refactor app store deployment form
- Support helm chart schema(#[schema-files](https://helm.sh/docs/topics/charts/#schema-files))

### BUG FIXES

- Fix the error when editing ingress annotations(#[1931](https://github.com/kubesphere/kubesphere/issues/1931))
- Fix container probes when editing in workload edit template modal
- Fix XSS security problems of the server-side templates
