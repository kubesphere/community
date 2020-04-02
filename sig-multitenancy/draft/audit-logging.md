## Audit-logging

First, implement a request filter.Decorates a http.Handler with audit logging information for all the requests coming to the server.Similar to K8s, we have more audit information that needs to be logged.

Request information to be audited: [request conetxt](../concepts-and-designs/requescontext.md)

Kubesphere filter example: https://github.com/kubesphere/kubesphere/blob/dev/pkg/apiserver/authentication/authenticators/basic/basic.go

K8s aduit filter: https://github.com/kubernetes/apiserver/blob/master/pkg/endpoints/filters/audit.go