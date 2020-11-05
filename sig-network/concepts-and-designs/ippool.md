## Overview

In Kubernetes, the following three types of networks are involved.

- Intra-cluster network，used by Cluster Service
- Cluster external network， used by LoadBalancer Service
- Pod network

The intra-cluster network, i.e. Service CIDR, is specified when the cluster is installed. When the Service is created, the `kube-apiserver` assigns an address from it and writes `spec.ClusterIP`. 

The remaining two network types are usually supported by cloud-provider and CNI plugins, but there is a wide variety of cloud vendors and CNI plugin types, and they all have their own implementations for address management. But here `KubeSphere` as a management platform, it must be docked to a variety of cloud vendors and CNI plugins, in order to provide a unified network address pool and address management,  and to provide a unified interface, so we developed this feature, the follow-up docking time, just need to write the corresponding plugins.

##  Principle

This function consists of two main parts, IPPool/IPAM.  IPPool is used to define the network address and its attributes, such as VLANs, etc. IPAM is used to define the allocation state of a segment of the network address.

### IPPool

Here's part of the IPPool data struct definition. 

```go

type IPPoolSpec struct {
	Type string `json:"type"`

	// The pool CIDR.
	CIDR string `json:"cidr"`

	// The first ip, inclusive
	RangeStart string `json:"rangeStart,omitempty"`

	// The last ip, inclusive
	RangeEnd string `json:"rangeEnd,omitempty"`

	// When disabled is true, IPAM will not assign addresses from this pool.
	Disabled bool `json:"disabled,omitempty"`

	// The block size to use for IP address assignments from this pool. Defaults to 26 for IPv4 and 112 for IPv6.
	BlockSize int `json:"blockSize,omitempty"`

	Workspace string `json:"workspace,omitempty"`
	Namespace string `json:"namespace,omitempty"`
}
```

`CIDR` is not allowed to overlap IPPool of the same type, the type identification is determined by the field `Type`, which needs to be registered in advance.

The scenarios here using IPPool fall into the following two categories

- Write your own network plugins

Usually the IPPool should contain information about the specific implementation of network connectivity, such as VLAN, IPIP, VXLAN, GRE, and so on.  Then your plug-in should listen to these configurations, set the corresponding network devices, and ensure that the addresses in the CIDR are interoperable. **IPPool now has built-in VLAN-related configuration.**

- Interface with existing network plugins

When docking an existing plugin， you need to implement the following interface.  

```go
type Provider interface {
	// canDelete indicates whether the address pool is being used or not.
	DeleteIPPool(pool *networkv1alpha1.IPPool) (canDelete bool, err error)
	CreateIPPool(pool *networkv1alpha1.IPPool) error
	UpdateIPPool(pool *networkv1alpha1.IPPool) error
	GetIPPoolStats(pool *networkv1alpha1.IPPool) (*networkv1alpha1.IPPool, error)
	SyncStatus(stopCh <-chan struct{}, q workqueue.RateLimitingInterface) error
}
```

The Calico docking module has now been implemented.  When the Calico module is initialized, it gets the configuration of `CALICO_IPV4POOL_IPIP`, `CALICO_IPV4POOL_VXLAN`, `CALICO_IPV4POOL_BLOCK_SIZE` etc. from the `Daemonset calico-node`, and fills the Calico ippool when `CreateIPPool` is called.

In addition, the status of the IPPool must be updated in real time, and the queue  `q workqueue.RateLimitingInterface` is used to notify the IPPool controller to call the `GetIPPoolStats` to get the status and then update it. 

### IPAM

IPAM is used to allocate addresses from the IPPool and provides the following interface.

```go
// ipam.Interface has methods to perform IP address management.
type Interface interface {
	// AutoAssign automatically assigns one IP addresse as specified by the
	// provided AutoAssignArgs.  AutoAssign returns the assigned IP addresse.
	AutoAssign(args AutoAssignArgs) (*current.Result, error)

	// ReleaseByHandle releases all IP addresses that have been assigned
	// using the provided handle.  
	ReleaseByHandle(handleID string) error

	GetUtilization(args GetUtilizationArgs) ([]*PoolUtilization, error)
}
```

The errors returned by the interface are as follows, when the error is `ErrNoQualifiedPool/ErrrUnknowIPPoolType` you should check your input, when other errors are present you should try again.

```go
var (
	ErrNoQualifiedPool  = errors.New("cannot find a qualified ippool")
	ErrNoFreeBlocks     = errors.New("no free blocks in ippool")
	ErrMaxRetry         = errors.New("Max retries hit - excessive concurrent IPAM requests")
	ErrUnknowIPPoolType = errors.New("unknow ippool type")
)
```