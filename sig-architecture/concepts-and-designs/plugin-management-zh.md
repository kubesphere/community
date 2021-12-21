### Plugin

插件仓库部署完成后，plugin-controller-mamnager 会定时拉取最新的 Chart 解析后生成 Plugin 对象，以供订阅。

```yaml
apiVersion: extensions.kubesphere.io/v1alpha1
kind: Plugin
metadata:
  name: devops
  labels:
    extensions.kubesphere.io/category=devops
status:
  phase: deployed
  currentVersion: v0.10.1
  versions:
  - description: DevOps plugin for KubeSphere.
    keywords:
    - devops
    maintainers:
    - email: devops.kubesphere.io
      name: kubesphere
    repo: builtin
    version: 0.10.0
    minKubeVersion: 1.17.0
  - description: DevOps plugin for KubeSphere.
    keywords:
    - devops
    maintainers:
    - email: devops.kubesphere.io
      name: kubesphere
    repo: builtin
    version: 0.10.1
    minKubeVersion: 1.17.0
```



### PluginVersion

插件可以同时存在多个版本，插件名称在同一个 Repo 中是唯一值

```yaml
apiVersion: extensions.kubesphere.io/v1alpha1
kind: PluginVersion
metadata:
  name: devops-v0.10.1
spec:
  description: DevOps plugin for KubeSphere.
  keywords:
  - devops
  maintainers:
  - email: devops.kubesphere.io
    name: kubesphere
  repo: builtin
  version: 0.10.0
  minKubeVersion: 1.17.0
  files:
  - NOTES.yaml
  - templates/deployments.yaml
```

### PluginVersion Files

Aggregated API，用于从 Repo 中直接加载 Helm Chart 中的数据 

文件列表

```
$ kubectl get --raw=/apis/packages.extensions.kubesphere.io/v1alpha1/pluginversions/devops-0.10.0/files
[
 "Chart.yaml",
 "README.md",
 "templates/NOTES.txt",
 "templates/deployment.yaml",
 "templates/hpa.yaml",
 "templates/ingress.yaml",
 "templates/service.yaml",
 "templates/serviceaccount.yaml",
 "templates/tests/test-connection.yaml",
 "values.yaml"
]%
```

获取单个文件

```
$ kubectl get --raw=/apis/packages.extensions.kubesphere.io/v1alpha1/pluginversions/xxx/files\?name=values.yaml
# Default values for test.
# This is a YAML-formatted file.
# Declare variables to be passed into your templates.

replicaCount: 1

image:
  repository: nginx
  pullPolicy: IfNotPresent
  # Overrides the image tag whose default is the chart appVersion.
  tag: ""

imagePullSecrets: []
nameOverride: ""
fullnameOverride: ""
```

### Subscription

通过订阅的方式安装插件，通过 Subscription 来控制安装卸载，启用、停用，状态同步，版本升级。

```yaml
apiVersion: extensions.kubesphere.io/v1alpha1
kind: Subscription
metadata:
  name: devops-0.10.0
spec:
  enabled: true
  plugin:
    name: devops 
    version: 0.10.0  # 通过更新版本触发 upgrade, rollback
  targetNamespace: kubesphere-devops-system
  config:
    foo: bar # 插件的配置信息
status:
  phase: deployed # unknown, superseded, failed, uninstalling, pending-install, pending-upgrade 或 pending-rollback
```


### Upgrade

TBD

### Dependency

TBD