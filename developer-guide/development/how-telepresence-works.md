# How Telepresence works

We can use Telepresence to help us running KubeSphere apiserver locally.
Here is the topology of our services(ks-apiserver and openpitrix). Through this 
we can understand how it works, which is conducive to our development.
​![telepresence-topology](/images/telepresence-topology.png)

## What telepresence has done
1. Create a proxy in kubernetes cluster. 
2. A two-way network tunel is established between the development machine and remote kubernetes cluster. Thus, your local process can connect with the remote kubernetes cluster.

## How a request is processed
If you want to debug your local ks-apiserver process with telepresence, your request will follow the dotted line.
The solid line represents how a request is processed in production environment.

## How to debug a service in kubesphere
1. Run telepresence like this 
```jshelllanguage
telepresence --namespace kubesphere-system --swap-deployment ks-apiserver --expose 9090:9090 --run go run ./cmd/ks-apiserver/apiserver.go
```
The option of `--swap-deployment` tells kubernetes to replace remote ks-apiserver with your local process in `kubesphere-system` namespace,
which means to scale the real ks-apiserver deployment to 0, and then create a new deployment that proxy your local ks-apiserver process.
Actually, the proxy in topology is the new deployment of ks-apiserver. When you exit from telepresence session, kubernetes will scale ks-apiserver 
deployment(proxy) to 0, and scale the real to 1 or other nums.