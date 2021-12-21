# 插件仓库

当我们通过 Docker Image 对 Helm Chart 进行打包的插件进行打包之后，可以将这个 Repo 部署到集群中

### Repository

定义 Repository 用于加载打包为 Docker Image 的插件，创建好 Repository 对象后，plugin-controller-manager 会部署该 Docker Image，以提供 Helm Repo（HTTP）、Plugin（Aggregated API） 相关的 API。

```yaml
apiVersion: extensions.kubesphere.io/v1alpha1
kind: Repository
metadata:
  name: builtin
spec:
  image: docker.io/kubespheredev/builtin:latest # 内置的仓库
  displayName: Builtin Repository
  publisher: admin@kubesphere.io
  updateStrategy: # 仓库的更新策略
    registryPoll:
      interval: 10m 
```

plugin-controller-manager 会部署 `docker.io/kubespheredev/builtin:latest`，并创建 builtin.kubesphere-system.svc 这个 Service，定时从 helm repo 拉取 Helm Chart, 读取 Helm Chart 中的元数据，进行数据校验，同时写入 Plugin、PluginVersion 对象，通过 Aggregated API 实现 pluginversions/files 这个 Aggregated API。

### Category

```yaml
apiVersion: extensions.kubesphere.io/v1alpha1
kind: Category
metadata:
  name: devops
spec:
  displayName: "DevOps"
  description: "DevOps"
```
