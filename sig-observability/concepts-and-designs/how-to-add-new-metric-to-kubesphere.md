# Why we need to add metrics to kubesphere

Metrics can provide insight into the behavior and health of our system. They represent the raw material used by monitoring system to build a holistic view of kubesphere, automate responses to changes, and alert human beings when required.

# How to add new metric

* 1. [Define the metric](#Define)
* 2. [Register the metric](#Register)
* 3. [Export the metric](#Export)


## 1. <a name='Define'></a>Define the metric
Define the metric in the  file `metric.go` of you package or somewhere else. 

 ```go
 package application

import (
	compbasemetrics "k8s.io/component-base/metrics"
	"kubesphere.io/kubesphere/pkg/utils/metrics"
 )

var (
    // add a counter metric
	appTemplateCreationCounter = compbasemetrics.NewCounterVec(
		&compbasemetrics.CounterOpts{
			Name:           "application_template_creation",  // metric name
			Help:           "Counter of application template creation broken out for each workspace, name and create state",    // metric help info
			StabilityLevel: compbasemetrics.ALPHA,  //represents the API guarantees for a given defined metric
		},
        //we want to export the namespace, name  and current state of the appTemplate
        []string{"workspace", "name", "state"},  // the  labels of the metric
	)
 )

```

## 2. <a name='Register'></a>Register the metric
```go
 package application
 import (
    "kubesphere.io/kubesphere/pkg/utils/metrics"
 )

 func init(){
    Register()
 }

 func Register() {
    metrics.MustRegister(appTemplateCreationCounter)
 }
```

## 3. <a name='Export'></a>Export the metric
```go
package application
func (c *appTemplateOperator) CreateApp(request *CreateAppRequest) {
      // export app template create metric with label values
     appTemplateCreationCounter.WithLabelValues("workspace", "Name", "failed").Inc()
}
```
