# AWS CSI Plugin

This is a plan list of integrating CSI of AWS into KubeSphere on **EKS**.

## Scope

In order to install KubeSphere on AWS, the following three AWS CSI plugins should be supported.

* [aws-ebs-csi](https://github.com/kubernetes-sigs/aws-ebs-csi-driver)
* [aws-efs-csi](https://github.com/kubernetes-sigs/aws-efs-csi-driver)
* [aws-fsx-csi](https://github.com/kubernetes-sigs/aws-fsx-csi-driver)

## Installation

As apps and plugins will be installed by Helm3 on KubeSphere 3.0, the AWS CSI plugins need support helm3 for installation.

## Version of Kubernetes

According to plugin compatibility matrix, the compatibility on Kubernetes **v1.15** will be checked for KubeSphere.

* [ebs-csi compatibility matrix](https://github.com/kubernetes-sigs/aws-ebs-csi-driver#ebs-csi-driver-on-kubernetes)
* [efs-csi compatibility matrix](https://github.com/kubernetes-sigs/aws-efs-csi-driver#efs-csi-driver-on-kubernetes)
* [fsx-csi compatibility matrix](https://github.com/kubernetes-sigs/aws-fsx-csi-driver#fsx-for-lustre-csi-driver-on-kubernetes)

## Feature

Currently, most features of CSI are put into effect on KubeSphere. The following items are covered:

* Volume Management
* Volume Expanding
* Volume Cloning
* Snapshot Management
* Topology

So, it will be checked if these features are supported on the AWS CSI plugins.
