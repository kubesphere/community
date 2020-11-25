# Controller Manager Quickstart

KubeSphere follows the [sample-controller](https://github.com/kubernetes/kubernetes/blob/master/staging/src/k8s.io/sample-controller) pattern to implement a controller for an active reconciliation process. It watches CustomResourceDefinition(CRD) desired state and actual state. Then, it sends instructions to try and make the current state be more like the desired state. 

> We won't discuss the pros and cons of the sample-controller comparing with Kubebuilder here. Just show you how to implement a controller.

**Note:** Read `sample-controller`'s [README.md](https://github.com/kubernetes/sample-controller/blob/master/README.md) and go through the `controller.go` before you begin.

## Defining types

To implement a controller, you should define your API Groups, Versions, and Kinds firstly. Please read more about the [Kubernetes API Conventions](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-architecture/api-conventions.md#websockets-and-spdy) if you want to understand those concepts deeper.

For example, the `Group` Kind that was defined under `iam.kubershpere.io` API Group as below:

```golang
// +genclient:nonNamespaced
// +genclient
// +k8s:deepcopy-gen:interfaces=k8s.io/apimachinery/pkg/runtime.Object
// +k8s:openapi-gen=true
// +kubebuilder:printcolumn:name="Workspace",type="string",JSONPath=".metadata.labels.kubesphere\\.io/workspace"
// +kubebuilder:resource:categories="group",scope="Cluster"

// Group is the Schema for the groups API
type Group struct {
	metav1.TypeMeta   `json:",inline"`
	metav1.ObjectMeta `json:"metadata,omitempty"`
    Status GroupStatus `json:"status,omitempty"`
	Spec   GroupSpec   `json:"spec,omitempty"`
}

// GroupSpec defines the desired state of Group
type GroupSpec struct {
    //We don't have Spec for Group.
}

```

In the comment, both `+k8s` and `+kubebuilder` markers are used in KubeSphere.

- `+k8s:deepcopy-gen` & `+genclient`: which is used by [k8s.io/code-generator](https://github.com/kubernetes/code-generator) to generate informers, listers, etc.
- `+kubebuilder`: which telling [controller-tools](https://github.com/kubernetes-sigs/controller-tools) to generate CRD YAMLs.

## Generate manifests and packages

There are directives defined in the Makefile, Which can help you generate codes automatically base on the markers we defined.

1. Generate manifests e.g. CRD, RBAC, etc.

```bash
make manifests
```
2. Generate typed client, informers, listers, and deep-copy packages

```bash
make clientset
```

## Implements a controller

If you have already learned the `sample-controller` as we suggested, you may found there are three major parts in the `sample-controller`'s implementation:
1. A `Controller` struct is defined to hold variables and a `NewController` function which use to create a `Controller` instance.
2. An asynchronous background worker runtime uses to process the queued items with re-try logic.
3. A `reconcile` function will contain your "do stuff" logic and some other helper functions.

Since the asynchronous background worker runtime is reusable, so we abstracted those functions into the `BaseController` struct in KubeSphere. You can compose the struct to inherit functions from it. 

Now you are ready to write your controller.

**First**, define a `Controller`, make sure the `controller.BaseController` is included. Declare necessary interfaces or types in the fields.
```golang 
type Controller struct {
	controller.BaseController
	k8sClient     kubernetes.Interface
	ksClient      kubesphere.Interface
	groupInformer iamv1alpha2informers.GroupInformer
	groupLister   iamv1alpha1listers.GroupLister
}
```

**Second**, Create a `NewController` function that use to create a `Controller` instance. In the function `NewController`, register a `Handler` that use to process reconcile logic. Meanwhile, you need to subscribe the informer's event by register the `Enqueue` function.

You can only subscribe to one informer as your primary resource. That's to say, only one kind of CRD can be put in the queue. If you need to subscribe to another related resource change event, create another function to handle it. And if it is owned by a primary resource, it should enqueue that primary resource for processing.

```golang 
// NewController creates Group Controller instance
func NewController(k8sClient kubernetes.Interface, ksClient kubesphere.Interface, groupInformer iamv1alpha2informers.GroupInformer) *Controller {

	ctl := &Controller{
		BaseController: controller.BaseController{
			Workqueue: workqueue.NewNamedRateLimitingQueue(workqueue.DefaultControllerRateLimiter(), "Group"),
			// workers will be started when all informer are syned.
			Synced:    []cache.InformerSynced{groupInformer.Informer().HasSynced},
			Name:      controllerName,
		},
		k8sClient:     k8sClient,
		ksClient:      ksClient,
		groupInformer: groupInformer,
		groupLister:   groupInformer.Lister(),
	}

	// Register a Handler to reconcile the spec and status
	ctl.Handler = ctl.reconcile

	// Set up Enqueue as event handler for when Group resources change
	groupInformer.Informer().AddEventHandler(cache.ResourceEventHandlerFuncs{
		AddFunc: ctl.Enqueue,
		UpdateFunc: func(old, new interface{}) {
			ctl.Enqueue(new)
		},
		DeleteFunc: ctl.Enqueue,
	})
	return ctl
}

```

**Last**, implement the `Start` interface to run the background. 

```golang 

func (c *Controller) Start(stopCh <-chan struct{}) error {
	return c.Run(1, stopCh)
}


func (c *Controller) reconcile(key string) error {
  // "do stuff" logic
}
```



## Resources

For further information about how to implement a controller:

- The `BaseController` code sample can be found in the pull request [#3138](https://github.com/kubesphere/kubesphere/pull/3138/files)
- The example [sample controller](https://github.com/kubernetes/sample-controller) shows a code example of a controller that uses the clients, listers, and informers generated by the`code-generator`.
- The article [Kubernetes Deep Dive: Code Generation for CustomResources](https://www.openshift.com/blog/kubernetes-deep-dive-code-generation-customresources) gives a step by step instructions on how to use `code-generator`.
- The Kubernetes official document gives a best practice about how to [Writing Controllers](https://github.com/kubernetes/community/blob/8cafef897a22026d42f5e5bb3f104febe7e29830/contributors/devel/controllers.md)
- To understand why only the status part of the custom resource should be updated, please refer to the [Kubernetes API conventions](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status).




