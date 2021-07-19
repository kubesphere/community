# KubeSphere Logging

This documentation contains backend development guide for interaction with key components behind KubeSphere logging system. KubeSphere logging system provides the functionality of log searching, downloading and store.

## File Tree

The listing below covers relevant code for logging.

```yaml
/cmd
  └─ks-apiserver
      └─app
          └─options       # initialize logging client when launching ks-apiserver
              ├─options.go
              └─validation.go
/pkg
  ├─api
  │  └─logging            # declare api response structure
  │      └─v1alpha2
  ├─kapis                  
  │  └─tenant             # register multi-tenant logging apis
  │      └─v1alpha2
  │          ├─handler.go
  │          └─register.go
  ├─models
  │  └─logging.go         # interact with the logging client
  └─simple
      └─client
          └─logging     
              ├─interface.go           # define logging client interfaces
              └─elasticsearch          # an elasticsearch implementation of logging client
                  ├─api_body.go        # defines elasticsearch api request/response body structures
                  ├─elasticsearch.go   
                  ├─options.go         # elasticsearch client options
                  └─versions           # implement logging interfaces by elasticsearch versions
                      ├─v5
                      ├─v6
                      └─v7
                   
```

## API Design

There are two types of APIs in logging, one for multi-tenant log searching (See [register.go](https://github.com/kubesphere/kubesphere/blob/v3.0.0/pkg/kapis/tenant/v1alpha2/register.go#L232-L255)), and the other for interacting with [Fluent Bit Operator CRD](https://github.com/kubesphere/fluentbit-operator) to configure log collection. For more information about Fluent Bit Operator CRD, please go to the project repo.