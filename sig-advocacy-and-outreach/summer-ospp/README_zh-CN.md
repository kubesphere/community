
>  [English](README.md)  | 中文

# 开源软件供应链点亮计划
[开源软件供应链点亮计划 - 暑期 2021](https://summer.iscas.ac.cn)，开源软件供应链点亮计划鼓励大家关注开源软件和开源社区，致力于培养和发掘更多优秀的开发者。
活动将在暑期进行，我们将与开源社区紧密合作，提供一对一的导师指导，邀请技术大牛开展线上免费讲座。
我们鼓励研究人员、开源爱好者、在校师生参与开源软件的开发与维护，促进开源软件的发展和优秀开源软件社区建设，
增加开源项目的活跃度，推进开源生态的发展。

## KubeSphere

KubeSphere 参与[开源软件供应链点亮计划 - 暑期 2021](https://summer.iscas.ac.cn/#/org/projectlist) 。您可以在本页找到我们的项目提案。或者您也可以向 KubeSphere 社区提交您的建议。

## 项目提案

| 项目 | 领域 | 技能 | 难 度 | 学生 |
| --- | --- | --- | --- | --- |
| [kubeSphere Jenkins 客户端重构](kubeSphere-jenkins-client-refactor_zh-CN.md) <br/>从 [KubeSphere](https://github.com/kubesphere/kubesphere/) 核心代码中的 DevOps 部分将 Jenkins 客户端代码分离开，或者，使用已有的 Jenkins 客户端。<br/>导师： [Rick](https://github.com/LinuxSuRen/), [JohnNiang](https://github.com/johnniang/) | DevOps | Golang，REST API/OpenAPI，Jenkins，Kubernetes | 中 | 吴晓涵 |
| [KubeSphere 集成 Tekton](kubeSphere-tekton-integration_zh-CN.md) <br/>集成 [Tekton](https://github.com/tektoncd/pipeline) 作为 [KubeSphere](https://github.com/kubesphere/kubesphere/) DevOps 可选的 CI/CD 引擎。 <br/>导师：[Rick](https://github.com/LinuxSuRen/)，[JohnNiang](https://github.com/johnniang/) | DevOps | Golang，Tekton，Jenkins，Kubernetes | 中 | 吴嘉皓 |
| [使用 iptables 的 NAT 规则暴露 K8s Loadbalancer 服务](expose-loadbalancer-services-using-iptables-nat-rules_zh-CN.md) <br/>为 [PorterLB](https://porterlb.io/) 提供一个更简单的模式：允许用户使用 Kubernetes 集群节点的 IP 地址和服务端口来暴露 LoadBalancer 服务。 <br/>导师： [Zhengyi Lai](https://github.com/zheng1) | Network              | Golang，Kubernetes，Linux network (iptables/IPVS) | 中 | 龙泓杙 |
| [Notification Manager 发送通知到 pushover](support-send-notifications-to-pushover_zh-CN.md)<br/>使 Notification Manager 可以发送通知消息到 pushover。<br/>导师：[benjaminhuo](https://github.com/benjaminhuo),[lei](https://github.com/wanjunlei) | Notification Manager | Golang，REST API，Kubernetes                        | 中 | 丁梓硕 |
| [集成 Gatekeeper](kubesphere-gatekeeper-integration_zh-CN.md) <br/>将 Gatekeeper 作为准入策略引擎集成到 KubeSphere。<br/>导师：[Hongming](https://github.com/wansir/), [Roland](https://github.com/rolandma1986/)| Security | Golang，React，OPA，Gatekeeper，Kubernetes | 中 | 汤贤赫 |
| [集成 SAML 认证](KubeSphere-SAML-integrations_zh-CN.md) <br/>集成 SAML 2.0 认证协议到 KubeSphere<br/>导师：[Hongming](https://github.com/wansir/), [Roland](https://github.com/rolandma1986/)| Security | Golang，REST API/OpenAPI，SAML | 低 | 无 |
| [OpenFunction 的函数构建器开发](OpenFunction-function-builder_zh-CN.md) <br>开发并优化函数构建器，使其可以识别 Python、Nodejs、Java、PHP（可选）、Rust（可选）语言，并将函数构建成可以运行在 OpenFunction 中的应用镜像。<br>导师：[Benjamin Huo](https://github.com/benjaminhuo)、[Fang Tian](https://github.com/tpiperatgod/) | Functions-as-a-Service | Golang，Tekton Cloud Native Buildpacks，OpenFunction | 中 | 马朋辉 |
| [OpenFunction 的 nodejs 函数框架开发](OpenFunction-function-framework-nodejs_zh-CN.md) <br>开发用于处理 nodejs 代码的函数框架，为用户的业务代码提供适用于云原生环境的多种工具套件。<br>导师：[Benjamin Huo](https://github.com/benjaminhuo)、[Fang Tian](https://github.com/tpiperatgod/) | Functions-as-a-Service | Golang，Tekton Cloud Native Buildpacks，OpenFunction，Nodejs | 中 | 林许亚伦 |
| [OpenFunction 项目官网开发](openfunction-website_zh-CN.md)<br>在项目导师的帮助下，为全新的 Serverless 开源项目 [OpenFunction](https://github.com/OpenFunction/OpenFunction) 从零开始搭建与开发项目的官方网站，并完成项目上线。<br>导师：[Feynman Zhou](https://github.com/FeynmanZhou)、[Sherlock](https://github.com/Sherlock113) | Website | JavaScript，HTML，CSS，Markdown | 低 | 张源易 |
| [KubeSphere 官网文档写作与本地化](document-localization_zh-CN.md) <br>在项目导师的帮助下，为开源项目 [KubeSphere](https://github.com/kubesphere/kubesphere) 撰写新的产品文档，根据用户需求为官方文档的本地化，将英文文档翻译成中文文档。<br>导师：[Feynman Zhou](https://github.com/FeynmanZhou)、刘金辉 | Website | Markdown、Hugo | 低 | 张杨茂 |
| [KubeSphere 项目官网优化](kubesphere-website_zh-CN.md)<br/>在项目导师的帮助下，为开源项目 [KubeSphere](https://github.com/kubesphere/kubesphere) 完善 KubeSphere 官网以及文档网站，实现部分功能特性发布到线上。<br>导师：[刘博](https://github.com/liuboaibc)、[Feynman Zhou](https://github.com/FeynmanZhou) | Website | JavaScript，HTML，CSS，Markdown | 低 | 刘宇乐 |

## 学生

* 5 月 24 日- 6 月 13 日是学生提交项目申请阶段，详情请查看 [学生指南](https://summer.iscas.ac.cn/help/student/)
* [开源软件供应链点亮计划 - 暑期 2021](https://summer.iscas.ac.cn/)

## 联系

- Slack [#sig-advocacy-and-outreach](https://kubesphere.slack.com/messages/sig-advocacy-and-outreach)
- 邮箱列表 [archive](https://groups.google.com/group/kubesphere-sig-advocacy-and-outreach/topics) | [subscribe](mailto:kubesphere-sig-advocacy-and-outreach+subscribe@googlegroups.com) | [unsubscribe](mailto:kubesphere-sig-advocacy-and-outreach+unsubscribe@googlegroups.com)

