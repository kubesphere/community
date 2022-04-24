# 项目

KubeEye Console2.0 前端页面开发

## 项目目标

* 开发 KubeEye Console2.0 插件管理功能的前端页面。

## 技术要求

* JavaScript、TypeScript、HTML、CSS
* React
* Docker、Kubernetes(背景知识)

## 项目背景

KubeEye 旨在发现 Kubernetes 上的各种问题，比如应用配置错误（使用 [OPA](https://github.com/open-policy-agent/opa) ）、集群组件不健康和节点问题（使用[Node-Problem-Detector](https://github.com/kubernetes/node-problem-detector)）。除了预定义的规则，它还支持自定义规则。

## 项目详情

KubeEye2.0 支持了以插件化的形式扩展监控规则。本项目即是 KubeEye 插件管理前端界面的开发。主要内容包括插件列表页、详情页开发，插件的安装、卸载、启动、停止等功能。

## 项目产出

* 插件管理界面开发

## 链接

* https://github.com/kubesphere/kubeeye
* https://github.com/kubesphere/kubeeye-console

## 快速入门

项目使用的组件库是 [KubeDesign](https://github.com/kubesphere/kube-design/tree/next)，你可以先看下文档和源码了解一下组件库的使用方法。
页面的设计在 [figma](https://www.figma.com/file/aDij53tnzKPr7dofRE54mX/%E9%A1%B9%E7%9B%AE_%E9%9B%86%E7%BE%A4%E5%B7%A1%E6%A3%80?node-id=627%3A19873) 上，你可以先看下将要实现的 ui 设计。
项目使用的技术栈是 Typescript、React，你可以提前熟悉上手。
项目的 1.0 版本仓库地址在 [kubeeye-console](https://github.com/kubesphere/kubeeye-console)， 你可以先熟悉下代码结构。

## 导师/联系方式

* [chenzhen](https://github.com/chenz24)
