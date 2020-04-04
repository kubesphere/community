---
title: "Release Notes For 2.0.2"
keywords: "kubernetes, docker, kubesphere, jenkins, istio, prometheus"
description: "KubeSphere Release Notes For 2.0.2"
---

KubeSphere 2.0.2 was released on July 9, 2019, which fixes known bugs and enhances existing feature. If you have installed versions of 1.0.x, 2.0.0 or 2.0.1, please download KubeSphere installer v2.0.2 to upgrade.

## What's New in 2.0.2

### Enhanced Features

- [API docs](/api-reference/api-docs/) are available on the official website.
- Block brute-force attacks.
- Standardize the maximum length of resource names.
- Upgrade the gateway of project (Ingress Controller) to the version of 0.24.1. Support Ingress grayscale release.

## List of Fixed Bugs

- Fix the issue that traffic topology displays resources outside of this project.
- Fix the extra service component issue from traffic topology under specific circumstances.
- Fix the execution issue when "Source to Image" reconstructs images under specific circumstances.
- Fix the page display problem when "Source to Image" job fails.
- Fix the log checking problem when Pod status is abnormal.
- Fix the issue that disk monitor cannot detect some types of volume mounting, such as LVM volume.
- Fix the problem of detecting deployed applications.
- Fix incorrect status of application component.
- Fix host node's number calculation errors.
- Fix input data loss caused by switching reference configuration buttons when adding environmental variables.
- Fix the rerun job issue that the Operator role cannot execute.
- Fix the initialization issue on IPv4 environment uuid.
- Fix the issue that the log detail page cannot be scrolled down to check past logs.
- Fix wrong APIServer addresses in KubeConfig files.
- Fix the issue that DevOps project's name cannot be changed.
- Fix the issue that container logs cannot specify query time.
- Fix the saving problem on relevant repository's secrets under certain circumstances.
- Fix the issue that application's service component creation page does not have image registry's secrets.
