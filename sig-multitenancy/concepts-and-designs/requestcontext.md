# Request Context

## User

UserInfo describes a user that has been authenticated to the system. In filter chain, userInfo in context can be obtained by calling `request.UserFrom(ctx)`.

The following fields are provided currently:

```go
type Info interface {
	// GetName returns the name that uniquely identifies this user among all
	// other active users.
	ßGetName() string
	// GetUID returns a unique value for a particular user that will change
	// if the user is removed from the system and another user is added with
	// the same name.
	GetUID() string
	// GetGroups returns the names of the groups the user is a member of
	GetGroups() []string

	// GetExtra can contain any additional information that the authenticator
	// thought was interesting.  One example would be scopes on a token.
	GetExtra() map[string][]string
}
```

## RequestInfo

RequesInfo holds information parsed from the http request. It will be used throughout the request chain. In filter chain, requestInfo in context can be obtained by calling `request.RequestInfoFrom(ctx)`. RequestInfo extended from `k8s.io/apiserver/pkg/endpoints/request/requestinfo.go`.

The following fields are provided currently:

```go
type RequestInfo struct {
	// IsResourceRequest indicates whether or not the request is for an API resource or subresource
	IsResourceRequest bool
	// Path is the URL path of the request
	Path string
	// Verb is the kube verb associated with the request for API requests, not the http verb.  This includes things like list and watch.
	// for non-resource requests, this is the lowercase http verb
	Verb string

	APIPrefix  string
	APIGroup   string
	APIVersion string
	Namespace  string
	// Resource is the name of the resource being requested.  This is not the kind.  For example: pods
	Resource string
	// Subresource is the name of the subresource being requested.  This is a different resource, scoped to the parent resource, but it may have a different kind.
	// For instance, /pods has the resource "pods" and the kind "Pod", while /pods/foo/status has the resource "pods", the sub resource "status", and the kind "Pod"
	// (because status operates on pods). The binding resource for a pod though may be /pods/foo/binding, which has resource "pods", subresource "binding", and kind "Binding".
	Subresource string
	// Name is empty for some verbs, but if the request directly indicates a name (not in body content) then this field is filled in.
	Name string
	// Parts are the path parts for the request, always starting with /{resource}/{name}
	Parts []string

	// IsKubernetesRequest indicates whether or not the request should be handled by kubernetes or kubesphere
	IsKubernetesRequest bool

	// Workspace of requested resource, for non-workspaced resources, this may be empty
	Workspace string

	// Cluster of requested resource, this is empty in single-cluster environment
	Cluster string
}
```
