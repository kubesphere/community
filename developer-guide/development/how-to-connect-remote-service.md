# Connect to remote service with Telepresence

[Telepresence](https://www.telepresence.io/) is an open source tool that lets you run a single service locally, while connecting the service to a remote Kubernetes cluster.

We can use Telepresence to help us running KubeSphere apiserver locally.
Make sure you have installed `socat` on all of your nodes or you will get some error while starting telepresence.
## 1. Install Telepresence

You can read the [official installation documentation](https://www.telepresence.io/reference/install.html) to install Telepresence.

## 2. Run Telepresence

Open your command line and run the command `telepresence`. Telepresence will help you to enter a bash connected to a remote Kubernetes cluster.

Test Telepresence with KubeSphere apigateway:

```bash
$ curl http://ks-apiserver.kubesphere-system
401 Unauthorized
```

## 3. Run your module in bash

Now your module can easily connect to remote services.

```bash
go run cmd/ks-apiserver/apiserver.go
```

## 4. Further more

You can use [Telepresence](how-telepresence-works.md) to replace services in the cluster for debugging. For more information, please refer to the [official documentation](https://www.telepresence.io/discussion/overview).