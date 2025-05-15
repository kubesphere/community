# 插件开发指南

## 开发插件

### 项目初始化

1. 通过 CLI 创建一个项目脚手架
   
TBD

### 前端页面的开发

1. 如何插入一个新的功能页面
2. 前端设计风格指南
   
TBD

### 后端 API 的开发

1. 后端 API 风格指南
2. API 权限控制
   
TBD

## 插件的打包与发布

插件开发完成之后，需要与依赖组件一起打包为 Helm Chart。

1. 一个插件打包为一个 Helm Chart
2. 一组插件打包为 Docker Image 之后可以进行发布

### Helm Chart 的目录结构

```bash
devops/
├── .helmignore  
├── Chart.yaml  # Helm chart 基本信息
├── LICENSE     
├── README.md   
├── values.yaml # 默认的配置信息
├── charts/      
└── templates/   
    ├── workloads.yaml      # 需要部署的工作负载
    ├── services.yaml       # 需要创建的 service 
    ├── extensions.yaml     # 定义 APIService, JSBundle 用于注册 API 与 js 文件
    ├── roletemplates.yaml  # 通过 role template CRD 动态注册权限控制项
    └── tests/
dmp/  # 可以同时打包发布多个插件
├── .helmignore  
├── Chart.yaml   
├── LICENSE     
├── README.md    
├── values.yaml  
├── charts/      
└── templates/   
    ├── workloads.yaml     
    ├── services.yaml      
    ├── extensions.yaml     
    ├── roletemplates.yaml
    └── tests/
Dockerfile # 将 charts 打包到 docker image 进行发布
```

### Chart.yaml 的定义

```yaml
apiVersion: v2
name: devops
version: v0.10.0
kubeVersion: v1.17.0
description: DevOps Plugin for KubeSphere.
type: application
keywords:
  - DevOps
home: https://kubesphere.io
sources:
  - https://github.com/kubesphere/ks-devops
dependencies: # chart 必要条件列表 （可选）
  - name: jenkins
    version: v0.0.1
    # repository: （可选）仓库URL () 或别名 ("@repo-name")
    # condition: （可选） 解析为布尔值的yaml路径，用于启用/禁用chart (e.g. subchart1.enabled )
    # tags:  （可选）
    #   - 用于一次启用/禁用 一组chart的tag
    # import-values:  （可选）
    #   - ImportValue 保存源值到导入父键的映射。每项可以是字符串或者一对子/父列表项
    # alias: （可选） chart中使用的别名。当你要多次添加相同的chart时会很有用
maintainers: 
  - name: kubesphere
    email: rick@Kubesphere.io
    url: https://github.com/linuxsuren
icon: 'data:image/png;base64, PHN2ZyBoZWlnaHQ9IjUxMnB0IiB2aWV3Qm94PSIwIDAgNTEyIDUxMi4wMDEiIHdpZHRoPSI1MTJwdCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJtNTEyIDI1NmMwIDE0MS4zODY3MTktMTE0LjYxMzI4MSAyNTYtMjU2IDI1Ni0xNDEuMzgyODEyIDAtMjU2LTExNC42MTMyODEtMjU2LTI1NnMxMTQuNjE3MTg4LTI1NiAyNTYtMjU2YzE0MS4zODY3MTkgMCAyNTYgMTE0LjYxMzI4MSAyNTYgMjU2em0wIDAiIGZpbGw9IiM1YTU0ZTAiLz48cGF0aCBkPSJtNTEwLjkyOTY4OCAyNzkuMzQ3NjU2LTkxLjM1NTQ2OS05MS4zNTkzNzUtNy41OTc2NTcgMTAuMTA5Mzc1LTEwNC45ODA0NjgtMTA0Ljk4NDM3NS02NC4xODc1IDEyMi45MTAxNTctMTQ0LjAwNzgxMyAyNi44MzU5MzcgMTI1Ljk5MjE4OCAxMjUuOTkyMTg3LTY2LjI4OTA2MyA0Ni44MTY0MDcgOTYuMzIwMzEzIDk2LjMxNjQwNmMuMzk0NTMxLjAwMzkwNi43ODUxNTYuMDE1NjI1IDEuMTc1NzgxLjAxNTYyNSAxMzMuNTExNzE5IDAgMjQzLjEzMjgxMi0xMDIuMjE0ODQ0IDI1NC45Mjk2ODgtMjMyLjY1MjM0NHptMCAwIiBmaWxsPSIjMzgzOGJhIi8+PHBhdGggZD0ibTE4NCA1MDEuNzE4NzVjMjIuODM5ODQ0IDYuNjc5Njg4IDQ3IDEwLjI4MTI1IDcyIDEwLjI4MTI1czQ5LjE2MDE1Ni0zLjYwMTU2MiA3Mi0xMC4yODEyNXYtMTQyLjcxODc1aC0xNDR6bTAgMCIgZmlsbD0iI2ZmYmVhYSIvPjxwYXRoIGQ9Im0yNTUuOTA2MjUgMzU5djE1M2guMDkzNzVjMjUgMCA0OS4xNjAxNTYtMy42MDE1NjIgNzItMTAuMjgxMjV2LTE0Mi43MTg3NXptMCAwIiBmaWxsPSIjZmFhNjhlIi8+PHBhdGggZD0ibTM4NS4xMjUgMTY5LjkxNzk2OWgtMjU4LjI1Yy0yMy4xMjUgMC00MS44NzUgMTguNzQ2MDkzLTQxLjg3NSA0MS44NzUgMCAyMy4xMjUgMTguNzUgNDEuODc1IDQxLjg3NSA0MS44NzVoMzEuNjI4OTA2djE2MmgxOTQuOTkyMTg4di0xNjJoMzEuNjI4OTA2YzIzLjEyODkwNiAwIDQxLjg3NS0xOC43NSA0MS44NzUtNDEuODc1IDAtMjMuMTI4OTA3LTE4Ljc0NjA5NC00MS44NzUtNDEuODc1LTQxLjg3NXptMCAwIiBmaWxsPSIjZmZkYTAwIi8+PHBhdGggZD0ibTM4NS4xMjUgMTY5LjkxNzk2OWgtMTI5LjIxODc1djI0NS43NWg5Ny41ODk4NDR2LTE2MmgzMS42Mjg5MDZjMjMuMTI4OTA2IDAgNDEuODc1LTE4Ljc1IDQxLjg3NS00MS44NzUgMC0yMy4xMjg5MDctMTguNzQ2MDk0LTQxLjg3NS00MS44NzUtNDEuODc1em0wIDAiIGZpbGw9IiNmZmIwMDAiLz48cGF0aCBkPSJtMzIwLjMzMjAzMSAxMzIuMzMyMDMxYzAgMzUuNTMxMjUtMjguODAwNzgxIDY0LjMzMjAzMS02NC4zMzIwMzEgNjQuMzMyMDMxcy02NC4zMzIwMzEtMjguODAwNzgxLTY0LjMzMjAzMS02NC4zMzIwMzFjMC0zNS41MjczNDMgMjguODAwNzgxLTY0LjMzMjAzMSA2NC4zMzIwMzEtNjQuMzMyMDMxczY0LjMzMjAzMSAyOC44MDQ2ODggNjQuMzMyMDMxIDY0LjMzMjAzMXptMCAwIiBmaWxsPSIjZmZmIi8+PHBhdGggZD0ibTI1NiA2OGMtLjAzMTI1IDAtLjA2MjUuMDAzOTA2LS4wOTM3NS4wMDM5MDZ2MTI4LjY2MDE1NmguMDkzNzVjMzUuNTMxMjUgMCA2NC4zMzIwMzEtMjguODAwNzgxIDY0LjMzMjAzMS02NC4zMzIwMzEgMC0zNS41MjczNDMtMjguODAwNzgxLTY0LjMzMjAzMS02NC4zMzIwMzEtNjQuMzMyMDMxem0wIDAiIGZpbGw9IiNlOWVkZjUiLz48cGF0aCBkPSJtMjMzLjY2MDE1NiAxMzIuMzMyMDMxYzAgNy45MTQwNjMtNi40MTQwNjIgMTQuMzI4MTI1LTE0LjMyODEyNSAxNC4zMjgxMjUtNy45MTAxNTYgMC0xNC4zMjgxMjUtNi40MTQwNjItMTQuMzI4MTI1LTE0LjMyODEyNSAwLTcuOTE0MDYyIDYuNDE3OTY5LTE0LjMyODEyNSAxNC4zMjgxMjUtMTQuMzI4MTI1IDcuOTE0MDYzIDAgMTQuMzI4MTI1IDYuNDE0MDYzIDE0LjMyODEyNSAxNC4zMjgxMjV6bTAgMCIgZmlsbD0iI2ZlODIwNSIvPjxwYXRoIGQ9Im0zMDYuOTk2MDk0IDEzMi4zMzIwMzFjMCA3LjkxNDA2My02LjQxNDA2MyAxNC4zMjgxMjUtMTQuMzI4MTI1IDE0LjMyODEyNS03LjkxNDA2MyAwLTE0LjMyODEyNS02LjQxNDA2Mi0xNC4zMjgxMjUtMTQuMzI4MTI1IDAtNy45MTQwNjIgNi40MTQwNjItMTQuMzI4MTI1IDE0LjMyODEyNS0xNC4zMjgxMjUgNy45MTQwNjIgMCAxNC4zMjgxMjUgNi40MTQwNjMgMTQuMzI4MTI1IDE0LjMyODEyNXptMCAwIiBmaWxsPSIjZmU2YTE2Ii8+PC9zdmc+'
appVersion: v0.10.0
annotations:
  extensions.kubesphere.io/foo: bar # 额外的注释信息
```

### 打包为 Docker Image 对插件进行分发

```dockerfile
FROM baseimage # Framwork 提供的 baseimage

WORKDIR /charts
COPY . /charts
RUN helm index . 
CMD ["serve"] # serve 一个 helm repo，并提供 grpc 接口，配合 Repository 实现 API Aggregation
```
