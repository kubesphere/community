# Helm package development tutorial

## The Chart File Structure
```
wordpress/
  Chart.yaml          # A YAML file containing information about the chart
  LICENSE             # OPTIONAL: A plain text file containing the license for the chart
  README.md           # OPTIONAL: A human-readable README file
  requirements.yaml   # OPTIONAL: A dependencies field defining chart dependencies
  values.yaml         # The default configuration values for this chart
  charts/             # A directory containing any charts upon which this chart depends.
  templates/          # A directory of templates that, when combined with values,
                      # will generate valid Kubernetes manifest files.
  templates/NOTES.txt # OPTIONAL: A plain text file containing short usage notes
  templates/_helpers.tpl # OPTIONAL:A place to put template helpers that you can re-use throughout the chart
  crds/               # OPTIONAL: Custom Resource Definitions
```

## The Chart.yaml File
The Chart.yaml file is required for a chart. It contains the following fields:
```
apiVersion: The chart API version (required)
name: The name of the chart (required)
version: A SemVer 2 version (required)
kubeVersion: A SemVer range of compatible Kubernetes versions (optional)
description: A single-sentence description of this project (optional)
type: It is the type of chart (optional)
keywords:
  - A list of keywords about this project (optional)
home: The URL of this projects home page (optional)
sources:
  - A list of URLs to source code for this project (optional)
dependencies: # A list of the chart requirements (optional)
  - name: The name of the chart (nginx)
    version: The version of the chart ("1.2.3")
    repository: The repository URL ("https://example.com/charts") or alias ("@repo-name")
    condition: (optional) A yaml path that resolves to a boolean, used for enabling/disabling charts (e.g. subchart1.enabled )
    tags: # (optional)
      - Tags can be used to group charts for enabling/disabling together
    enabled: (optional) Enabled bool determines if chart should be loaded
    import-values: # (optional)
      - ImportValues holds the mapping of source values to parent key to be imported. Each item can be a string or pair of child/parent sublist items.
    alias: (optional) Alias usable alias to be used for the chart. Useful when you have to add the same chart multiple times
maintainers: # (optional)
  - name: The maintainers name (required for each maintainer)
    email: The maintainers email (optional for each maintainer)
    url: A URL for the maintainer (optional for each maintainer)
icon: A URL to an SVG or PNG image to be used as an icon (optional).
appVersion: The version of the app that this contains (optional). This needn't be SemVer.
deprecated: Whether this chart is deprecated (optional, boolean)
```
## The README.md File
A README for a chart should be formatted in Markdown (README.md), and should generally contain:
* Introduction
* Prerequisites
* Installing the Chart
* Uninstalling the Chart
* Configuration

## Chart Dependencies
In Helm, one chart may depend on any number of other charts. These dependencies can be dynamically linked using the dependencies field in Chart.yaml or brought in to the charts/ directory and managed manually.
```
dependencies:
  - name: apache
    version: 1.2.3
    repository: http://example.com/charts
    alias: new-subchart-1
```
* Name: The name field is the name of the chart you want.
* Version: The version field is the version of the chart you want.
* repository: The repository field is the full URL to the chart repository. Note that you must also use helm repo add to add that repo locally.
* alias：One can use alias in cases where they need to access a chart with other name(s).
#### Once you have defined dependencies, you can run helm dependency update and it will use your dependency file to download all the specified charts into your charts/ directory for you.
#### You can define true/false in values.yaml to determine whether the dependency package is enabled, such as
```
apache:
  enabled: true
```
#### A dependency can be an unpacked chart directory. 
#### Dependent execution order: refer to the k8s load self-starting principle, so we can not care about the execution.Actually cross-execute.
#### Note: helm2 is described by requirements.yaml, helm3 is directly described in chart.yaml.

## templates/k8s resource
* There are multiple deployment objects under templates and you can name them differently.
* Execution order: refer to the k8s load self-starting principle, so we can not care about the execution.
* The actual execution order is:
```
var InstallOrder KindSortOrder = []string{
    "Namespace",
    "NetworkPolicy",
    "ResourceQuota",
    "LimitRange",
    "PodSecurityPolicy",
    "PodDisruptionBudget",
    "Secret",
    "ConfigMap",
    "StorageClass",
    "PersistentVolume",
    "PersistentVolumeClaim",
    "ServiceAccount",
    "CustomResourceDefinition",
    "ClusterRole",
    "ClusterRoleList",
    "ClusterRoleBinding",
    "ClusterRoleBindingList",
    "Role",
    "RoleList",
    "RoleBinding",
    "RoleBindingList",
    "Service",
    "DaemonSet",
    "Pod",
    "ReplicationController",
    "ReplicaSet",
    "Deployment",
    "HorizontalPodAutoscaler",
    "StatefulSet",
    "Job",
    "CronJob",
    "Ingress",
    "APIService",
}
```
* There are two ways to do this: one is to set pre-install, and the other is to set weights:

pre-install hooks，such as：
```
apiVersion: v1
kind: Service
metadata:
  name: foo
  annotations:
    "helm.sh/hook": "pre-install"
```
set weights,such as:
```
annotations:
    "helm.sh/hook-weight": "5"
```

## values.yaml
* Release.Name: The name of the release (not the chart)
* Release.Namespace: The namespace the chart was released to.
* Release.Service: The service that conducted the release.
* chart :The contents of the Chart.yaml. Thus, the chart version is obtainable as Chart.Version and the maintainers are in Chart.Maintainers.
* There are multiple deployment objects under templates, you can name them with different names, and then you can define values under values.yaml with different names., as defined in the following format：

```
mysql:
  name: 
  image:
    repository: 
    tag: 
    pullPolicy:

redis:
  name: 
  image:
    repository: 
    tag: 
    pullPolicy:
```
## helm template
The helm template syntax is nested between "{{" ""}}", three of which are common
```
.Values.*
usually defined in a values.yaml file and --set （--set Priority maximum）。
.Release.*
Read from the metadata running Release, and a new Release is generated with each installation
template * .
Read from the _helpers.tpl file and define a named template using the define function
.Chart.*
Read from the chart.yaml file
```

## Template functions and pipes
```
 A | pipe, similar to a Linux pipe, works the same in the following example.
{{ quote .Values.favorite.drink }} and  {{ .Values.favorite.drink | quote }}
 Default sets the default value
drink: {{ .Values.favorite.drink | default “tea” | quote }}
 Indent template function, blank space to the left, blank two Spaces to the left
{{ include "mychart_app" . | indent 2 }}
 Include function, similar to template
For example, in _helpers.tpl, define templates are referred to in resource objects.


{{- define "mychart.labels" }}
  labels:
    generator: helm
    date: {{ now | htmlDate }}
{{- end }}

apiVersion: v1
kind: ConfigMap
metadata:
  name: {{ .Release.Name }}-configmap
  {{- template "mychart.labels" }}
data:
```
## Use files in templates

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: conf
data:
{{ (.Files.Glob "foo/*").AsConfig | indent 2 }}
```
* The contents of the foo directory under the chart root configured as configmap

## Template flow control
* In common use:
if/else condition control
with Scope of control
range cycle control 
* For example, variables are defined in: values.yaml, and the ConfigMap.Values. Favorite loop controls parameters.

```
favorite:
  drink: coffee
  food: pizza

apiVersion: v1
kind: ConfigMap
metadata:
  name: {{ .Release.Name }}-configmap
data:
  myvalue: "Hello World"
  {{- range $key, $val := .Values.favorite }}
  {{ $key }}: {{ $val | quote }}
  {{- end}}
```
* Use the if/else syntax in the deployment.yaml, such as: -end end flag, with "-" in double brackets.
```
{{- if .Values.image.repository -}}
image: {.Values.image.repository}
{{- else -}}
image: "***/{{ .Release.Name }}:{{ .Values.image.version }}"
{{- end -}}
```


