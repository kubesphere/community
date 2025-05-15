# 基于 KubeSphere 实现 CodeSpace 功能

## 项目目标
基于 vscode-server 实现 Github CodeSpace 类似的 Online Web IDE 能力，为 KubeSphere 私有云环境提供服务增强。

## 项目背景
Github CodeSpace 是个非常有创新性的能力，它同时支持 DevContainer 协议，自动完成开发环境的部署，这对于团队新人非常友好，节省了环境准备的痛苦经历，把更多注意力集中在代码开发中。

但是在私有云环境中，轻量级的 CodeSpace 在企业内部，特别是对于一些轻量级项目来说，非常实用方便；我们将通过此项目为 KubeSphere 提供 CodeSpace 支持。

## 项目详情

### 开发内容
- 自定义 CRD 描述整个项目的配置
- 仿照 DevContainer 自定义项目中配置文件配置
- 开发 Operator 监控 CRD 配置，基于项目项目配置创建 DEV POD
- 通过共享存储存储和保存项目源码

### 技术实现
- 使用 python 语言开发 Kubernetes Operator
- 自定义 CRD 配置及 合理的默认值
- 开发 Kubesphere 插件，实现简单前端界面
- 支持项目至少为 python，java， nodejs 项目

### 项目产出
1. 使用 kopf 框架开发 Kubernetes Operator
1.1 编程语言: Python；开发框架: kopf
1.2 自定义 CRD 实现项目配置及适当的默认值
1.3 实现 Operator 核心逻辑并验证

2. 实现与 KubeSphere 控制台集成的 Web 前端界面
2.1：前端技术: JavaScript、React (与 KubeSphere 前端集成)
2.2：基于 Luban 框架实现与 KubeSphere 控制台集成

3. 文档支持
3.1 编写完整的项目文档和使用说明书
3.2 编写测试项目及测试步骤


### 导师联系

- KubeSphere 广州站站长: **裴振飞**

- 联系邮箱：peizhenfei@cvte.com

### 详细链接

[开源软件供应链点亮计划](https://summer-ospp.ac.cn/org/prodetail/256690520?list=org&navpage=org)
