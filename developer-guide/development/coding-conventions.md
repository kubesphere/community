# KubeSphere Conventions

> This doc mostly from [coding conventions](https://github.com/kubernetes/community/blob/master/contributors/guide/coding-conventions.md) of Kubernetes community. Some modifications are made to be applicable for our case. 

## Coding conventions
* Bash
    * Ensure that build, release, test, and cluster-management scripts run on macOS

* Go
    * Make sure you followed style from [Go Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments) and [Effective Go](https://golang.org/doc/effective_go).
    * Comment your code.
        * [Go's commenting conventions](https://blog.golang.org/godoc)
        * If reviewers ask questions about why the code is the way it is, that's the sign that comments might be helpful.
    * Command-line flags should use dashes, not underscores.
    * Naming
        * Please consider package name when selecting an interface name, and avoid redundancy.
            * e.g.: `storeg.Interface` is better than `storage.StorageInterface`
        * Do not use uppercase characters, underscores, or dashes in package names.
        * Please consider parent directory name when choosing a package name.
            * so pkg/controllers/autoscaler/foo.go should say package autoscaler not package autoscalercontroller.
            * Importers can use a different name if they need to disambiguate.

* [Logging](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-instrumentation/logging.md) 

    * Use [klog](http://godoc.org/github.com/kubernetes/klog) instead of [log](http://golang.org/pkg/log/), klog is globally perferred to log for better runtime control.
    * Shared libraries, such as `kubsphere client-go`, should not use `klog.ErrorS()` and `klog.InfoS()`, but just return `error`, because client libraries may be used in CLI UIs that wish to control output.
    * `klog` conventions
        * klog.ErrorS() - Errors should be used to indicate unexpected behaviors in code, like unexpected errors returned by subroutine function calls. 
        * klog.InfoS() - Structured logs to the INFO log. It has multiple levels:
            * klog.V(0) - Generally useful for this to ALWAYS be visible to an operator
            * klog.V(1) - A reasonable default log level if you don't want verbosity.
            * klog.V(2) - Useful steady state information about the service and important log messages that may correlate to significant changes in the system. This is the recommended default log level for most systems.
            * klog.V(3) - Extended information about changes
            * klog.V(4) - Debug level verbosity
            * klog.V(5) - Trace level verbosity

## Testing conventions
* All new packages and most new significant functionality must come with unit tests.
* Table-driven tests are preferred for testing multiple scenarios/inputs; for example, see [TestNamespaceAuthorization](https://git.k8s.io/kubernetes/test/integration/auth/auth_test.go)
* Significant features should come with integration (test/integration) and/or end-to-end (test/e2e) tests
* Unit tests must pass on macOS and Linux platforms.
* Avoid waiting for a short amount of time (or without waiting) and expect an asynchronous thing to happen (e.g. wait for 1 seconds and expect a Pod to be running). Wait and retry instead.
 
## Directory and file conventions
* Avoid package sprawl. Find an appropriate subdirectory for new packages. 
    * Libraries with no more appropriate home belong in new package subdirectories of pkg/util
* Avoid general utility packages. Packages called "util" are suspect. Instead, derive a name that describes your desired function. For example, the utility functions dealing with waiting for operations are in the "wait" package and include functionality like Poll. So the full name is wait.Poll
* All filenames should be lowercase.
* Go source files and directories use underscores, not dashes
    * Package directories should generally avoid using separators as much as possible (when packages are multiple words, they usually should be in nested subdirectories).
* **Document directories** and filenames should use dashes rather than underscores

