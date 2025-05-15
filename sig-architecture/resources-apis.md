# New List and Get APIs for Custom Resource Definition

KubeSphere API server provided more Frontend friendly APIs than the Kubernetes API, which provided API with filtering, sorting, and paging abilities. So KubeSphere Console interacts with ks-apiserver directly instead of Kubernetes API.

We should provide an extensible and compatible API mechanism for the KubeSphere API server that:

- All the CRDs(or CRDs with a kapis server label) can be registered to the ks-apiserver automatically
- Use the same RBAC authorization by registering an endpoint that qualified the GVR URL format
- Can be customized with filtering, sorting, etc, when necessary.

## Background

Currently, the "resources.kubesphere.io" Kapis group is the common List/Get APIs for the Custom Resources, which provides APIs with filtering, sorting, and paging abilities. However, The "resources/v1alpha3.Interface" needs to be implemented for the CRDs to register to the API group. If we digger into the Interface implementation, we can find that more than 60% of codes are duplicated, and many CRDs don't need to implement the Filter, Comparer for itself.

Another disadvantage of this group is that GV is different from the CRD, which means that we had to grant the permission separately. If we can register the API GRV as same as the CRD, we can save a lot of work during grant permission.

## The new API endpoints

All the endpoints are listed in the bellow tables:

| URL | Scope | comments |
| -------- | -------- | -------- |
| kapis/{group}/{version}/{kind}/  | Cluster/Namespace | Query cluster resources or Query namespaced resources in all namspaces |
| kapis/{group}/{version}/{kind}/{name}  | Cluster  | Get a cluster resource |
| kapis/{group}/{version}/namespaces/{namespace}/{kind}/ | Namespace |Query resources in the namespace|
| kapis/{group}/{version}/namespaces/{namespace}/{kind}/{name} | Namespace | Get a namespace resource |
| kapis/{group}/{version}/workspaces/{workspace}/{kind}/ | Workspace | Query cluster resources that belong to workspace |
| kapis/{group}/{version}/workspaces/{workspace}/{kind}/{name} | Workspace | Get a cluster resource that belong to workspace |

> The GV will be ignored when the New Group Version is already existed.

**Group** is as same as the CRD's Groups. There are multi **Versions** could be exist for a CRD, but only the `Storaged` and `Served` version will be served in ks-apiserver.

## Register CRD Schemes

Not all the CRDs are served by ks-apiserver for performance reasons. Only the CRDs with "kubesphere.io/resource-served" label will be served by the ks-apiserver.

```yaml
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  annotations:
    kubesphere.io/resource-scope: workspaced
  labels:
    kubesphere.io/resource-served: "true"
spec:
  scope: Cluster
  group: cert-manager.io
  name:
...
```

> A Cluster scope CRD in the Kubernetes can be isolated to the workspace Space scope in KubeSphere.

After applying the label and annotation, the KS API server starts to serve each enabled CRD at an HTTP REST endpoint. In the above example, the API versions are available at `/kapis/cert-manager.io/v1`.

## Register custom filters or sorter

There are many built-in filters and sorters available by default. Such as:

- Sort By: name, createTime
- Filter By: name, uid, ownerReference,ownerKind, label, annotation

> Example: namespace?page=1&limit=10&name=ab&sortBy=creationTimestamp

But you may still need to add some other filters by yourself. In this case, you need to do it as the following steps:

### Step 1. Register CRD to the Controller Runtime

Find the following code snippet under `cmd/ks-apiserver/app/options/options.go`. Register your CRD definetion as bellow:

```	
func (s *ServerRunOptions) NewAPIServer(stopCh <-chan struct{}) (*apiserver.APIServer, error) {
    ...
    sch := scheme.Scheme
	if err := apis.AddToScheme(sch); err != nil {
		klog.Fatalf("unable add APIs to scheme: %v", err)
	}

	apiServer.RuntimeCache, err = runtimecache.New(apiServer.KubernetesClient.Config(), runtimecache.Options{Scheme: sch})
	if err != nil {
		klog.Fatalf("unable to create controller runtime cache: %v", err)
	}
    ...
```

### Step 2. Create new Filters
Create a new go file under the `models` folder with the following template. Then you can implement the logic yourself.

```go
package test

import (
	metav1 "k8s.io/apimachinery/pkg/apis/meta/v1"
	"k8s.io/apimachinery/pkg/runtime"
	"kubesphere.io/kubesphere/pkg/models/crds"
)
func init() {
	crds.Filters[schema.GroupVersionKind{Group: "kubesphere.io", Version: "v1", Kind: "test"}] = filter
	crds.Comparers[schema.GroupVersionKind{Group: "kubesphere.io", Version: "v1", Kind: "test"}] = compare
    //	crds.Transformers[schema.GroupVersionKind{Group: "kubesphere.io", Version: "v1", Kind: "test"}] = []crds.TransformFunc{transform}
}

func compare(left, right metav1.Object, field query.Field) bool {

	leftDeployment, ok := left.(*v1.Deployment)
	if !ok {
		return false
	}

	rightDeployment, ok := right.(*v1.Deployment)
	if !ok {
		return false
	}

	switch field {
	case 'your filed':
		// your logic
	default:
		return crds.DefaultObjectMetaCompare(leftDeployment, rightDeployment, field)
	}
}

func filter(object metav1.Object, filter query.Filter) bool {
	deployment, ok := object.(*v1.Deployment)
	if !ok {
		return false
	}

	switch filter.Field {
	case 'your filed':
		// your logic;
	default:
		return crds.DefaultObjectMetaFilter(deployment, filter)
	}
}
```

### Step 3. import the go filter's go package

Since we use `init()` to register the filter, we need to import the package when registering the API Group. Suggest to register under it `pkg/kapis/crd/crd.go`.
