# Upgrading Kubernetes and KubeSphere in KubeKey
## Introduction
[KubeKey](https://github.com/kubesphere/kubekey) is the new installer of KubeSphere. This document focuses on upgrading Kubernetes and KubeSphere with Kubekey.

Cases of plan support:
* KubeKey Cluster
* Non-KubeKey Cluster &ensp; (Cluster deployed with kubeadm)

## KubeKey Cluster
### Allinone
Upgrading cluster with a specified version.
```shell script
./kk upgrade [--with-kubernetes version] [--with-kubesphere version] 
```
* Support upgrading Kubernetes only.
* Support upgrading KubeSphere only.
* Support upgrading Kubernetes and KubeSphere.

### Multi-nodes
Upgrading cluster with a specified configuration file.
```shell script
./kk upgrade [--with-kubernetes version] [--with-kubesphere version] [(-f | --file) path]
```
* If `--with-kubernetes` or `--with-kubesphere` is specified, the configuration file will be also updated.
* Use `-f` to specify the configuration file which was generated for cluster creation.

## Non-KubeKey Cluster
### Allinone
Same as KubeKey Cluster.
### Multi-nodes
Getting cluster info and generating kubekey's configuration file.
```shell script
./kk create config [--from-cluster] [(-f | --file) path] [--kubeconfig path]
```
* `--from-cluster` means fetching cluster's information from an existing cluster. 
* `-f` refers to the path where the configuration file is generated.
* `--kubeconfig` refers to the path where the kubeconfig. 
* After generating the configuration file, some parameters need to be filled in, such as the ssh information of the nodes.

After completing the generated configuration file, upgrading cluster using the same method as KubeKey Cluster.