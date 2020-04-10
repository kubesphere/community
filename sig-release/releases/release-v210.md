---
title: "Release Notes For 2.1.0"
keywords: "kubernetes, docker, kubesphere, jenkins, istio, prometheus"
description: "KubeSphere Release Notes For 2.1.0"
---

KubeSphere 2.1.0 was released on Nov 11th, 2019, which fixes known bugs, adds some new features and brings some Enhancement. If you have installed versions of 2.0.x, please upgrade it and enjoy the better user experience of v2.1.0.

## Installer Enhancement

- Decouple some components, enabling components including DevOps, service mesh, app store, logging, alerting and notification are optional and pluggable
- Add Grafana (v5.2.4) as the optional component
- Upgrade Kubernetes to 1.15.5. It is also compatible with 1.14.x and 1.13.x
- Upgrade  [OpenPitrix](https://openpitrix.io/)  to v0.4.5
- Upgrade the log forwarder Fluent Bit to v1.3.2
- Upgrade Jenkins to v2.176.2
- Upgrade Istio to 1.3.3
- Optimize the high availability for core components

## App Store

### Features

Support upload / test / review / deploy / publish/ classify / upgrade / deploy and delete apps, and provides nine built-in applications

### Upgrade & Enhancement

- The application repository configuration is migrated from global to each workspace
- Support add application repository to share applications in a workspace

## Storage

### Features

- Support Local Volume with Dynamic provisioning
- Provide the real-time monitoring feature for QingCloud block storage

### Upgrade & Enhancement

QingCloud CSI is adapted to CSI 1.1.0, supports upgrade, topology, create or delete a snapshot, it also supports create PVC based on a snapshot

### BUG Fixes

Fix the StorageClass list display problem

## Observability

### Features

- Support for collecting the file logs on the disk,  it is used for the Pod which preserve the logs as the file on the disk
- Support integrating with external ElasticSearch 7.x
- Ability to search logs including Chinese words
- Add initContainer log display
- Ability to export logs
- Support for canceling the notification from alerting

### UPGRADE & ENHANCEMENT
- Optimize the speed of log search
- Optimize the hints when the logging service is abnormal
- Optimize the information when the monitoring metrics request is abnormal
- Support pod anti-affinity rule for Prometheus

### BUG FIXES
- Fix the mistaken highlights in the logs search result
- Fix log search not matching phrases correctly
- Fix the issue that log could not be retrieved for a deleted workload when it is searched by workload name
- Fix the issue where the results were truncated when the log is highlighted
- Fix some metrics exceptions: node `inode`, maximum pod tolerance
- Fix the issue with an incorrect number of alerting targets
- Fix filter failure problem of multi-metric monitoring
- Fix the problem of no logging and monitoring information on taint nodes (Adjust the toleration attributes of node-exporter and fluent-bit to deploy on all nodes by default, ignoring taints)

## DevOps

### Features

- Add support for branch exchange and git log export in S2I
- Add B2I, ability to build Binary/WAR/JAR package and release to Kubernetes
- Support dependency cache for the pipeline, S2I, and B2I
- Support delete Kubernetes resource action in `kubernetesDeploy` step
- Multi-branch pipeline supports trigger other pipelines when create or delete the branch

### Upgrades & Enhancement
- Support BitBucket in the pipeline
- Support Cron script validation in the pipeline
- Support Jenkinsfile syntax validation
- Support custom the link in SonarQube
- Support event trigger build in the pipeline
- Optimize the agent node selection in the pipeline
- Accelerate the start speed of the pipeline
- Use dynamical volume as the work directory of the Agent in the pipeline, also contributes to Jenkins [#589](https://github.com/jenkinsci/kubernetes-plugin/pull/598)
- Optimize the Jenkins kubernetesDeploy plugin, add more resources and versions (v1, app/v1, extensions/v1beta1、apps/v1beta2、apps/v1beta1、autoscaling/v1、autoscaling/v2beta1、autoscaling/v2beta2、networking.k8s.io/v1、batch/v1beta1、batch/v2alpha1), also contributes to Jenkins [#614](https://github.com/jenkinsci/kubernetes-plugin/pull/614)
- Add support for PV, PVC, Network Policy in deploy step of the pipeline, also contributes to Jenkins [#87](https://github.com/jenkinsci/kubernetes-cd-plugin/pull/87)、[#88](https://github.com/jenkinsci/kubernetes-cd-plugin/pull/88)

### Bug Fixes

- Fix the issue that 400 bad request in GitHub Webhook
- incompatible change: DevOps Webhook's URL prefix is changed from `/webhook/xxx` to `/devops_webhook/xxx`

## Authentication and authority

### Features

Support sync and authenticate with AD account

### Upgrades & Enhancement

- Reduce the LDAP component's RAM consumption
- Add protection against brute force attacks

### Bug Fixes

- Fix LDAP connection pool leak
- Fix the issue where users could not be added in the workspace
- Fix sensitive data transmission leaks

## User Experience

### Features

Ability to wizard management of projects (namespace) that are not assigned to the workspace

### Upgrades & Enhancement

- Support bash-completion in web kubectl
- Optimize the host information display
- Add connection test of the email server
- Add prompt on resource list page
- Optimize the project overview page and project basic information
- Simplify the service creation process
- Simplify the workload creation process
- Support real-time status update in the resource list
- optimize YAML editing
- Support image search and image information display
- Add the pod list to the workload page
- Update the web terminal theme
- Support container switching in container terminal  
- Optimize Pod information display, and add Pod scheduling information
- More detailed workload status display

### Bug Fixes

- Fix the issue where the default request resource of the project is displayed incorrectly
- Optimize the web terminal design, make it much easier to find
- Fix the Pod status update delay
- Fix the issue where a host could not be searched based on roles
- Fix DevOps project quantity error in workspace detail page
- Fix the issue with the workspace list pages not turning properly
- Fix the problem of inconsistent result ordering after query on workspace list page
