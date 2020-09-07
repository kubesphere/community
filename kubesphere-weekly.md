# KubeSphere Weekly: News and Updates in Community

This document records the news and updates from the past weeks.

## KubeSphere Weekly #3: September 07, 2020

### Community & Documentation

- 3.0.0 GA announcement: KubeSphere 3.0.0 GA: Born for Hybrid Cloud Apps ( [En](https://kubesphere.io/news/kubesphere-3.0.0-ga-announcement/) / [Zh](https://mp.weixin.qq.com/s/CAqCFTT3Xtcfat-Z7eMhUA) )
- Implement the installation testing of KubeSphere 3.0.0 on [Digital Ocean](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-do/), [AWS EKS](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-eks/), and Bare Metal (WIP) with contributors. We have completed the related installation guides for them.
- Write the outline of user guide and administrator guide for KubeSphere 3.0.0, and we are looking for community users to get involved in the translation of documentation v3.0.0.
- Test the installation and integration with openEuler OS, and we are struggling to contribute KubeSphere Installer into openEuler community, see this [PR](https://gitee.com/openeuler/kubekey/pulls/1/files) for details.

## KubeSphere Weekly #2: August 23, 2020

### Website

- The documentation site for v3.0.0 is now available, you can preview the new documentation site [here](https://v3-0.docs.kubesphere.io/docs/).

### Community

- We organized the community users and partners to join the installation testing on some popular infrastructures and contribute to installation guide. Currently, we have **18** contributors joined and picked some of the tasks, see this [doc](https://github.com/kubesphere/community/blob/master/sig-docs/installation/community-collaboration-for-v3.0.0.md) for details
- We have tested the Porter v0.3.0 with Layer2 and BGP, and we also integrated Porter chart into KubeSphere, which makes it easy for users to install and try Porter. Porter v0.3.0 will be officially released in this week.
- We are preparing for the KubeSphere installer which is tailored for openEuler OS.

### Documentation

We have completed the installer testing and installed KubeSphere on some popular infrastructures, the following documents are also contributed by contributors.

- [KubeSphere on Azure AKS](https://v3-0.docs.kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-ks-on-aks/)
- [KubeSphere on VMware vSphere](https://v3-0.docs.kubesphere.io/zh/docs/installing-on-linux/on-premise/install-kubesphere-on-vmware-vsphere/)
- [KubeSphere on HuaweiCloud CCE](https://v3-0.docs.kubesphere.io/zh/docs/installing-on-kubernetes/hosted-kubernetes/install-ks-on-huawei-cce/)
- [KubeSphere on Azure VM Instance](https://deploy-preview-138--kubesphere-v3.netlify.app/docs/installing-on-linux/public-cloud/install-ks-on-azure-vms/)
- [KubeSphere on Google GKE](https://v3-0.docs.kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-on-gke/)
- [KubeSphere HA on QingCloud](https://github.com/kubesphere/docs.kubesphere.io/blob/master/content/en/installation/kubesphere-on-qingcloud-instance.md)

## KubeSphere Weekly #1: August 16, 2020

### Website

- The design and development of documentation site for v3.0.0 is almost ready, you can preview the new documentation site [here](https://deploy-preview-126--hugo-first.netlify.app/docs).

### Community

- We organized the community users and partners to join the installation testing on some popular infrastructures and contribute to installation guide. Currently, we have 14 contributors joined and picked some of the tasks, see this [doc](https://github.com/kubesphere/community/blob/master/sig-docs/installation/community-collaboration-for-v3.0.0.md) for details
- We have tested the Porter v0.3.0 with Layer2 and BGP, and we also integrated Porter chart into KubeSphere, which makes it easy for users to install and try Porter.
- Published an user case study: ZaloPay is running their Merchant Platform on KubeSphere to support hundreds of millions of users ([Chinese](https://mp.weixin.qq.com/s/vg1XbW3VPmdXAWKbGPxuUw)|[English](https://kubesphere.io/case/vng/)).
- Published a blog: Kubernetes Multicluster and Federation on KubeSphere ([Chinese](https://mp.weixin.qq.com/s/8EvA_-lSTpbOT-hq7PG5IA)|[English](https://github.com/kubesphere/website/pull/110/files)).
- APISIX helm chart has been contributed to KubeSphere Application Store by their PMC, see this [PR](https://github.com/kubesphere/helm-charts/pull/76) for details.
- Jenkins Chinese Community has ran two projects on KubeSphere.

### Documentation

- Community collaboration: We are preparing the documents for [Installing KubeSphere on some popular infrastructures](https://github.com/kubesphere/community/blob/master/sig-docs/installation/community-collaboration-for-v3.0.0.md).
- Improved AWS Quick Start Guide - KubeSphere on AWS EKS (Word)
- Write the introduction and use cases for KubeSphere v3.0.0, see these [PRs](https://github.com/kubesphere/docs.kubesphere.io/pull/753) for details.
