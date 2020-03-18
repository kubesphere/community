# KubeSphere File Tree

This document describes the directory structure of the KubeSphere backend repository.

```yaml
├── api // automatically generated API documentation
│   ├── api-rules
│   ├── ks-openapi-spec // REST API documentation provided by KubeSphere apiserver
│   └── openapi-spec // REST API documentation provided by KubeSphere apiserver
├── build // Dockerfile
│   ├── hypersphere
│   ├── ks-apigateway
│   ├── ks-apiserver
│   ├── ks-controller-manager
│   ├── ks-iam
│   └── ks-network
├── cmd // main applications for KubeSphere
│   ├── controller-manager  // KubeSphere Controller Manger, used to reconcile KubeSphere CRD
│   │   └── app
│   ├── hypersphere
│   ├── ks-apigateway // KubeSphere API gateway
│   │   └── app
│   ├── ks-apiserver // KubeSphere REST API server
│   │   └── app
│   ├── ks-iam // KubeSphere IAM service
│   │   └── app
│   └── ks-network
├── config // CRD config files
│   ├── crds // CRD yaml files
│   ├── default // kustomization yaml files
│   ├── manager // controller manager yaml files
│   ├── rbac // RBAC yaml files
│   ├── samples // CRD sample
│   └── webhook // webhook yaml files
├── docs
│   ├── en
│   │   ├── concepts-and-designs
│   │   └── guides
│   └── images
├── hack // script files to help people develop
│   └── lib
├── pkg // library code.
│   ├── api // structure definitions for REST APIs
│   │   ├── devops
│   │   ├── logging
│   │   └── monitoring
│   ├── apigateway
│   │   └── caddy-plugin
│   ├── apis // structure definitions for CRDs
│   │   ├── devops
│   │   ├── network
│   │   ├── servicemesh
│   │   └── tenant
│   ├── apiserver // REST API parameter processing
│   │   ├── components
│   │   ├── devops
│   │   ├── git
│   │   ├── iam
│   │   ├── logging
│   │   ├── monitoring
│   │   ├── openpitrix
│   │   ├── operations
│   │   ├── quotas
│   │   ├── registries
│   │   ├── resources
│   │   ├── revisions
│   │   ├── routers
│   │   ├── runtime
│   │   ├── servicemesh
│   │   ├── tenant
│   │   ├── terminal
│   │   ├── workloadstatuses
│   │   └── workspaces
│   ├── client // automatically generated CRD client
│   │   ├── clientset
│   │   ├── informers
│   │   └── listers
│   ├── constants // common constants
│   ├── controller // controller manager reconciliation logic
│   │   ├── application
│   │   ├── clusterrolebinding
│   │   ├── destinationrule
│   │   ├── job
│   │   ├── namespace
│   │   ├── network
│   │   ├── s2ibinary
│   │   ├── s2irun
│   │   ├── storage
│   │   ├── virtualservice
│   │   └── workspace
│   ├── db // database ORM framework
│   │   ├── ddl
│   │   ├── schema
│   │   └── scripts
│   ├── gojenkins // Jenkins Go client
│   │   ├── _tests
│   │   └── utils
│   ├── informers
│   ├── kapis // REST API registration
│   │   ├── devops
│   │   ├── iam
│   │   ├── logging
│   │   ├── monitoring
│   │   ├── openpitrix
│   │   ├── operations
│   │   ├── resources
│   │   ├── servicemesh
│   │   ├── tenant
│   │   └── terminal
│   ├── models // data processing part of REST API
│   │   ├── components
│   │   ├── devops
│   │   ├── git
│   │   ├── iam
│   │   ├── kubeconfig
│   │   ├── kubectl
│   │   ├── log
│   │   ├── metrics
│   │   ├── nodes
│   │   ├── openpitrix
│   │   ├── quotas
│   │   ├── registries
│   │   ├── resources
│   │   ├── revisions
│   │   ├── routers
│   │   ├── servicemesh
│   │   ├── status
│   │   ├── storage
│   │   ├── tenant
│   │   ├── terminal
│   │   ├── workloads
│   │   └── workspaces
│   ├── server // data processing part of REST API
│   │   ├── config
│   │   ├── errors
│   │   ├── filter
│   │   ├── options
│   │   └── params
│   ├── simple // common clients
│   │   └── client
│   ├── test
│   ├── utils // common utils
│   │   ├── hashutil
│   │   ├── idutils
│   │   ├── iputil
│   │   ├── jsonutil
│   │   ├── jwtutil
│   │   ├── k8sutil
│   │   ├── net
│   │   ├── readerutils
│   │   ├── reflectutils
│   │   ├── signals
│   │   ├── sliceutil
│   │   ├── stringutils
│   │   └── term
│   ├── version
│   └── webhook
├── test // e2e test code
│   └── e2e
└── tools // tools to generate API docs
    ├── cmd
    │   ├── crd-doc-gen // gen CRD API docs
    │   └── doc-gen // gen REST API docs
    └── lib
```
