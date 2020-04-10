---
title: "Release Notes For 2.1.1"
keywords: "kubernetes, docker, kubesphere, jenkins, istio, prometheus"
description: "KubeSphere Release Notes For 2.1.1"
---

KubeSphere 2.1.1 was released on Feb 23rd, 2020, which has fixed known bugs and brought some enhancements. For the users who have installed versions of 2.0.x or 2.1.0, make sure to read the user manual carefully about how to upgrade before doing that, and feel free to raise any questions on [GitHub](https://github.com/kubesphere/kubesphere/issues).

## What's New in 2.1.1

## Installer

### UPGRADE & ENHANCEMENT

- Support Kubernetes v1.14.x、v1.15.x、v1.16.x、v1.17.x，also solve the issue of Kubernetes API Compatibility#[1829](https://github.com/kubesphere/kubesphere/issues/1829)
- Simplify the steps of installation on existing Kubernetes, and remove the step of specifying cluster's CA certification, also specifying Etcd certification is no longer mandatory step if users don't need Etcd monitoring metrics
- Backup the configuration of CoreDNS before upgrading

### BUG FIXES

- Fix the issue of importing apps to App Store

## App Store

### UPGRADE & ENHANCEMENT

- Upgrade OpenPitrix to v0.4.8

### BUG FIXES

- Fix the latest version display issue for the published app #[1130](https://github.com/kubesphere/kubesphere/issues/1130)
- Fix the column name display issue in app approval list page #[1498](https://github.com/kubesphere/kubesphere/issues/1498)
- Fix the searching issue by app name/workspace #[1497](https://github.com/kubesphere/kubesphere/issues/1497)
- Fix the issue of failing to create app with the same name of previously deleted app #[1821](https://github.com/kubesphere/kubesphere/pull/1821) #[1564](https://github.com/kubesphere/kubesphere/issues/1564)
- Fix the issue of failing to deploy apps in some cases #[1619](https://github.com/kubesphere/kubesphere/issues/1619) #[1730](https://github.com/kubesphere/kubesphere/issues/1730)

## Storage

### UPGRADE & ENHANCEMENT

- Support CSI plugins of Alibaba Cloud and Tencent Cloud

### BUG FIXES

- Fix the paging issue of storage class list page #[1583](https://github.com/kubesphere/kubesphere/issues/1583) #[1591](https://github.com/kubesphere/kubesphere/issues/1591)
- Fix the issue that the value of imageFeatures parameter displays '2' when creating ceph storage class #[1593](https://github.com/kubesphere/kubesphere/issues/1593)
- Fix the issue that search filter fails to work in persistent volumes list page #[1582](https://github.com/kubesphere/kubesphere/issues/1582)
- Fix the display issue for abnormal persistent volume #[1581](https://github.com/kubesphere/kubesphere/issues/1581)
- Fix the display issue for the persistent volumes which associated storage class is deleted #[1580](https://github.com/kubesphere/kubesphere/issues/1580) #[1579](https://github.com/kubesphere/kubesphere/issues/1579)

## Observability

### UPGRADE & ENHANCEMENT

- Upgrade Fluent Bit to v1.3.5 #[1505](https://github.com/kubesphere/kubesphere/issues/1505)
- Upgrade Kube-state-metrics to v1.7.2
- Upgrade Elastic Curator to v5.7.6 #[517](https://github.com/kubesphere/ks-installer/issues/517)
- Fluent Bit Operator support to detect the location of soft linked docker log folder dynamically on host machines
- Fluent Bit Operator support to manage the instance of Fluent Bit by declarative configuration through updating the ConfigMap of Operator
- Fix the issue of sort orders in alert list page #[1397](https://github.com/kubesphere/kubesphere/issues/1397)
- Adjust the metric of container memory usage with 'container_memory_working_set_bytes'

### BUG FIXES

- Fix the lag issue of container logs #[1650](https://github.com/kubesphere/kubesphere/issues/1650)
- Fix the display issue that some replicas of workload have no logs on container detail log page #[1505](https://github.com/kubesphere/kubesphere/issues/1505)
- Fix the compatibility issue of Curator to support ElasticSearch 7.x #[517](https://github.com/kubesphere/ks-installer/issues/517)
- Fix the display issue of container log page during container initialization #[1518](https://github.com/kubesphere/kubesphere/issues/1518)
- Fix the blank node issue when these nodes are resized #[1464](https://github.com/kubesphere/kubesphere/issues/1464)
- Fix the display issue of components status in monitor center, to keep them up-to date #[1858](https://github.com/kubesphere/kubesphere/issues/1858)
- Fix the wrong monitoring targets number in alert detail page #[61](https://github.com/kubesphere/console/issues/61)

## DevOps

### BUG FIXES

- Fix the issue of UNSTABLE state not visible in the pipeline #[1428](https://github.com/kubesphere/kubesphere/issues/1428)
- Fix the format issue of KubeConfig in DevOps pipeline #[1529](https://github.com/kubesphere/kubesphere/issues/1529)
- Fix the image repo compatibility issue in B2I, to support image repo of Alibaba Cloud #[1500](https://github.com/kubesphere/kubesphere/issues/1500)
- Fix the paging issue in DevOps pipelines' branches list page #[1517](https://github.com/kubesphere/kubesphere/issues/1517)
- Fix the issue of failing to display pipeline configuration after modifying it #[1522](https://github.com/kubesphere/kubesphere/issues/1522)
- Fix the issue of failing to download generated artifact in S2I job #[1547](https://github.com/kubesphere/kubesphere/issues/1547)
- Fix the issue of [data loss occasionally after restarting Jenkins]( https://kubesphere.com.cn/forum/d/283-jenkins)
- Fix the issue that only 'PR-HEAD' is fetched when binding pipeline with GitHub #[1780](https://github.com/kubesphere/kubesphere/issues/1780)
- Fix 414 issue when updating DevOps credential #[1824](https://github.com/kubesphere/kubesphere/issues/1824)
- Fix wrong s2ib/s2ir naming issue from B2I/S2I #[1840](https://github.com/kubesphere/kubesphere/issues/1840)
- Fix the issue of failing to drag and drop tasks on pipeline editing page #[62](https://github.com/kubesphere/console/issues/62)

## Authentication and Authorization

### UPGRADE & ENHANCEMENT

- Generate client certification through CSR #[1449](https://github.com/kubesphere/kubesphere/issues/1449)

### BUG FIXES

- Fix content loss issue in KubeConfig token file #[1529](https://github.com/kubesphere/kubesphere/issues/1529)
- Fix the issue that users with different permission fail to log in on the same browser #[1600](https://github.com/kubesphere/kubesphere/issues/1600)

## User Experience

### UPGRADE & ENHANCEMENT

- Support to edit SecurityContext in workload editing page #[1530](https://github.com/kubesphere/kubesphere/issues/1530)
- Support to configure init container in workload editing page #[1488](https://github.com/kubesphere/kubesphere/issues/1488)
- Add support of startupProbe, also add periodSeconds, successThreshold, failureThreshold parameters in probe editing page #[1487](https://github.com/kubesphere/kubesphere/issues/1487)
- Optimize the status update display of Pods #[1187](https://github.com/kubesphere/kubesphere/issues/1187)
- Optimize the error message report on console #[43](https://github.com/kubesphere/console/issues/43)

### BUG FIXES

- Fix the status display issue for the Pods that are not under running status #[1187](https://github.com/kubesphere/kubesphere/issues/1187)
- Fix the issue that the added annotation can't be deleted when creating service of QingCloud LoadBalancer #[1395](https://github.com/kubesphere/kubesphere/issues/1395)
- Fix the display issue when selecting workload on service editing page #[1596](https://github.com/kubesphere/kubesphere/issues/1596)
- Fix the issue of failing to edit configuration file when editing 'Job' #[1521](https://github.com/kubesphere/kubesphere/issues/1521)
- Fix the issue of failing to update the service of 'StatefulSet' #[1513](https://github.com/kubesphere/kubesphere/issues/1513)
- Fix the issue of image searching for QingCloud and Alibaba Cloud image repos #[1627](https://github.com/kubesphere/kubesphere/issues/1627)
- Fix resource ordering issue with the same creation timestamp #[1750](https://github.com/kubesphere/kubesphere/pull/1750)
- Fix the issue of failing to edit configuration file when editing service #[41](https://github.com/kubesphere/console/issues/41)
