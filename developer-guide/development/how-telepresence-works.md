# How Telepresence works

We can use Telepresence to help us running KubeSphere apiserver locally.
Here is the toplogy of our services(ks-apiserver and openpitrix).Through this toplogy
we can understand how it works, which is conducive to our development.
​![telepresence-toplogy](/images/telepresence-toplogy.png)

## What has Telepresence has done
1. Created a proxy in kubernetes cluster. 
2. A two-way network tunel is established between the development machine and remote kubernetes cluster.thus,your local process can connect with the remote kubernetes cluster.

## How a request is processed
If you want to debug your local ks-apiserver process with telepresence, your request will follow the dotted line.
The solid line represents how a request is processed in production environment.
