# QuickStart on developing ks-apiserver.

KubeSphere apiserver is based on [go-restful](https://github.com/emicklei/go-restful). This document explains how to develop api with ks-apiserver from scratch.
If you are interested in developing controller-manager, see [sample-controller](https://github.com/kubernetes/sample-controller)
and [kubebuilder](https://github.com/kubernetes-sigs/kubebuilder).

## Prerequisites

### Go

KubeSphere is based on [Kubernetes](https://github.com/kubernetes/kubernetes). Both of them are written in [Go](http://golang.org/). If you don't have a Go development environment, please [set it up](http://golang.org/doc/code.html) first.

| Kubernetes     | requires Go |
|----------------|-------------|
| 1.13+          | 1.12&lt;=go&lt;=1.14|

> Tips:
>
> - Ensure your GOPATH and PATH have been configured in accordance with the Go
environment instructions.
> - It's recommended to install [macOS GNU tools](https://www.topbug.net/blog/2013/04/14/install-and-use-gnu-command-line-tools-in-mac-os-x) when using MacOS for development.

### Docker

KubeSphere components are often deployed as containers in Kubernetes. If you need to rebuild the KubeSphere components in the Kubernetes cluster, you'll need to [install Docker](https://docs.docker.com/install/) in advance.

### Dependency Management

KubeSphere uses [Go Modules](https://github.com/golang/go/wiki/Modules) to manage dependencies in the `vendor/` tree.

> Note: KubeSphere uses `go module` to manage dependencies, but the development process still relies on `GOPATH`
> In the CRD development process, you need to use tools to automatically generate code. The tools used by KubeSphere still need to rely on `GOPATH`.
> For Chinese contributors who are going to pull the go module, you are recommended to use [goproxy.cn](https://goproxy.cn) as the proxy.

### Kubesphere

See [how to install kubesphere](https://kubesphere.io/docs/).

## Hello KubeSphere
```bash
git clone https://github.com/kubesphere/kubesphere.git
cd kubesphere && mkdir -p pkg/kapis/hellokubesphere/v1alpha1 && cd pkg/kapis/hellokubesphere/v1alpha1
```
Create a file named `handler.go`. In this tutorial, it only returns a http response with "hello-kubesphere", you can also write your custom logic.  
```go
package hellokubesphere

import "github.com/emicklei/go-restful"

type handler struct {}

func newHandler() handler{
	return handler{}
}

func (h handler) HelloKubeSphere (req *restful.Request, resp *restful.Response) {
	resp.WriteAsJson(HelloResponse{
		Message: "hello kubesphere",
	})
}

type HelloResponse struct {
	Message string `json:"message"`
}
```
Once you have completed your logic part, you need to design your api path and http method and so on with a file named register.go.
See more details on [go-restful](https://github.com/emicklei/go-restful).

```go
package hellokubesphere

import (
	"net/http"

	"github.com/emicklei/go-restful"
	"k8s.io/apimachinery/pkg/runtime/schema"

	"kubesphere.io/kubesphere/pkg/api"
	"kubesphere.io/kubesphere/pkg/apiserver/runtime"
)

const (
	GroupName = "example.kubesphere.io"
)

var GroupVersion = schema.GroupVersion{Group: GroupName, Version: "v1alpha1"}

func AddToContainer(container *restful.Container) error {
	webservice := runtime.NewWebService(GroupVersion)
	handler := newHandler()

	webservice.Route(webservice.GET("/hello-kubesphere").
		Reads("").
		To(handler.HelloKubeSphere).
		Returns(http.StatusOK, api.StatusOK, HelloResponse{})).
		Doc("Api for hello-kubesphere")

	container.Add(webservice)

	return nil
}
```
Cause you have created a folder named v1alpha1, you need to set Version to v1alpha1.
See more details on [GVK](https://book.kubebuilder.io/cronjob-tutorial/gvks.html).<br>
Once you have created those two files, you still need to register your api into go-restful.
Go back to kubesphere root dir and edit pkg/apiserver/apiserver.go.<br>
Put the following line at the end of installKubeSphereAPIs function. <br>
Kubesphere has strict access control, see more about [access-control-and-account-management](https://v3-0.docs.kubesphere.io/docs/access-control-and-account-management/).

```go
urlruntime.Must(hellokubesphere.AddToContainer(s.container))
```
In this tutorial, you will use `admin` account to skip access control.

Congratulations,  you're one step closer to running ks-apiserver.

## Test

```bash
make test
```

## Building Ks-Apiserver

Go back kubesphere root dir and run `make ks-apiserver`.

If all goes well, you can get a ks-apiserver binary file under bin/cmd folder.

## Understand KubeSphere core's configuration

KubeSphere uses [viper](https://github.com/spf13/viper) to manage the configuration. KubeSphere supports setting up using command line arguments and configuration files.

> We recommend you use a configuration file during local development.

KubeSphere apiserver needs to communicate with many modules. When you run KubeSphere, you can choose to configure the modules you care about only.

During the development of KubeSphere apiserver, you must configure at least the relevant part of Kubernetes to ensure that KubeSphere apiserver can be started.

Below is a sample configuration of KubeSphere apiserver.

You can get the content by executing 

```bash
kubectl -n kubesphere-system get cm kubesphere-config -o yaml
```

> Note: 
>
> - In the default configuration, we use Kubernetes service name to access the service.
> - In a remote cluster, you may need to use external network exposure to connect to the cluster's internal services.
> - Or you can refer to the [documentation](how-to-connect-remote-service.md) to use `telepresence` to connect to remote services.
> - In this tutorial, you are assumed to running ks-apiserver out of cluster with telepresence.


```yaml
kubernetes:
  kubeconfig: "/root/.kube/config"
  master: https://192.168.0.5:6443
  $qps: 1e+06
  burst: 1000000
authentication:
  authenticateRateLimiterMaxTries: 10
  authenticateRateLimiterDuration: 10m0s
  loginHistoryRetentionPeriod: 168h
  maximumClockSkew: 10s
  multipleLogin: False
  kubectlImage: kubesphere/kubectl:v1.0.0
  jwtSecret: "xxx"
ldap:
  host: openldap.kubesphere-system.svc:389
  managerDN: cn=admin,dc=kubesphere,dc=io
  managerPassword: admin
  userSearchBase: ou=Users,dc=kubesphere,dc=io
  groupSearchBase: ou=Groups,dc=kubesphere,dc=io
redis:
  host: redis.kubesphere-system.svc
  port: 6379
  password: ""
  db: 0
s3:
  endpoint: http://minio.kubesphere-system.svc:9000
  region: us-east-1
  disableSSL: true
  forcePathStyle: true
  accessKeyID: openpitrixminioaccesskey
  secretAccessKey: openpitrixminiosecretkey
  bucket: s2i-binaries
mysql:
  host: mysql.kubesphere-system.svc:3306
  username: root
  password: password
  maxIdleConnections: 100
  maxOpenConnections: 100
  maxConnectionLifeTime: 10s
devops:
  host: http://ks-jenkins.kubesphere-devops-system.svc/
  username: admin
  password: xxx
  maxConnections: 100
openpitrix:
  runtimeManagerEndpoint:    "hyperpitrix.openpitrix-system.svc:9103"
  clusterManagerEndpoint:    "hyperpitrix.openpitrix-system.svc:9104"
  repoManagerEndpoint:       "hyperpitrix.openpitrix-system.svc:9101"
  appManagerEndpoint:        "hyperpitrix.openpitrix-system.svc:9102"
  categoryManagerEndpoint:   "hyperpitrix.openpitrix-system.svc:9113"
  attachmentManagerEndpoint: "hyperpitrix.openpitrix-system.svc:9122"
  repoIndexerEndpoint:       "hyperpitrix.openpitrix-system.svc:9108"
multicluster:
  enable: true
  agentImage: kubesphere/tower:v0.1.0
  proxyPublishService: tower.kubesphere-system.svc
monitoring:
  endpoint: http://prometheus-operated.kubesphere-monitoring-system.svc:9090
logging:
  host: http://elasticsearch-logging-data.kubesphere-logging-system.svc:9200
  indexPrefix: ks-logstash-log
events:
  host: http://elasticsearch-logging-data.kubesphere-logging-system.svc:9200
  indexPrefix: ks-logstash-events
auditing:
  enable: true
  host: http://elasticsearch-logging-data.kubesphere-logging-system.svc:9200
  indexPrefix: ks-logstash-auditing
alerting:
  endpoint: http://alerting-client-server.kubesphere-alerting-system.svc:9200/api/
notification:
  endpoint: http://notification.kubesphere-alerting-system.svc:9200
```

The KubeSphere core module will read the `kubesphere.yaml` file from the current directory, if not found, then search the `/etc/kubesphere` directory for the file, then load the configuration at startup.

Put the `kubesphere.yaml` under cmd/ks-apiserver folder.

## Install telepresence
See [how-to-connect-remote-service](how-to-connect-remote-service.md).

## Run  Ks-Apiserver out of cluster with telepresence

```bash
cd cmd/ks-apiserver
telepresence --namespace  kubesphere-system --swap-deployment ks-apiserver --run go run apiserver.go
```

Once you have seen logs like `Start listening on :9090`, that means you have run ks-apiserver successfully!

Verify your api is working by executing

```bash
curl -u admin:P@88w0rd localhost:9090/kapis/example.kubesphere.io/v1alpha1/hello-kubesphere
```
If you got the following message, you have completed developing your own API from scratch.

```json
{
    "message": "hello kubesphere"
}
```

## Building Images

Go back kubesphere root dir.

```bash
# Make sure you have have already executed 'make ks-apiserver' before building images
# $REPO is the docker registry to push to
# $Tag is the tag name of the docker image
# The full go build process will be executed in the Dockerfile, so you may # need to set GOPROXY in it.
docker build -f build/ks-apiserver/Dockerfile -t $REPO/ks-apiserver:$TAG .
```


> **NOTE:** If you get the following error while building images.

```bash
Step 3/5 : RUN apk add --no-cache ca-certificates
 ---> Running in e68559053901
fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/community/x86_64/APKINDEX.tar.gz
WARNING: Ignoring http://dl-cdn.alpinelinux.org/alpine/v3.11/main/x86_64/APKINDEX.tar.gz: BAD signature
WARNING: Ignoring http://dl-cdn.alpinelinux.org/alpine/v3.11/community/x86_64/APKINDEX.tar.gz: BAD signature
ERROR: unsatisfiable constraints:
  ca-certificates (missing):
    required by: world[ca-certificates]
The command '/bin/sh -c apk add --no-cache ca-certificates' returned a non-zero code: 1
```


Please make sure you have access to alpinelinux.org. Then you can push your own images to any repositories.
