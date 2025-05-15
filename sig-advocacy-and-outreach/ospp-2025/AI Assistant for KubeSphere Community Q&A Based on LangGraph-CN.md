# 基于 LangGraph 实现的 KubeSphere 社区问答 AI 助手


## 项目目标
基于 LangGraph 和 Milvus 向量数据库开发一个智能问答系统，整合 KubeSphere 社区的知识库、文档和常见问题，构建 Agentic RAG 工作流，为用户提供准确、实时的技术支持和解答，提升社区用户体验和技术支持效率。

## 项目背景
随着 KubeSphere 社区的快速发展，用户对技术支持和问题解答的需求日益增长。传统的文档检索和人工解答方式已无法满足高效率、高质量的服务需求。利用大语言模型和向量数据库技术，构建一个基于 Agentic RAG 的智能问答系统，可以极大提升社区支持效率，让用户能够快速获取准确的技术信息，同时减轻社区维护者的负担。

## 项目详情

### 开发内容
- 构建基于 KubeSphere 文档、GitHub issues 和社区讨论的知识库
- 利用 Milvus 向量数据库存储和索引文档内容
- 设计基于 LangGraph 的 Agentic RAG 工作流，实现完整的问答对话过程
- 开发自适应检索策略，提高回答准确性和相关性
- 开发问答系统的 API 接口，支持与 KubeSphere 控制台的集成
- 实现上下文感知的对话系统，支持多轮交互和问题深入探讨

### 技术实现
- 使用 LangGraph 构建 Agentic RAG 工作流，包括查询分析、文档检索、答案生成和自我验证等步骤
- 利用 Milvus 进行高效的相似性搜索，支持大规模文档检索
- 部署硅基流动平台免费模型（Qwen2.5、GLM-4 等），确保系统可用性和性能
- 构建反馈机制，持续优化回答质量
- 实现多语言支持，满足全球社区用户需求

### 项目产出
1. 开发基于 LangGraph 的 Agentic RAG 工作流核心
1.1：构建 KubeSphere 社区知识库并接入 Milvus 向量数据库
1.2：开发适配 Qwen2.5/GLM-4 等开源模型的问答接口
2. 实现与 KubeSphere 控制台集成的 Web 前端界面
2.1：开发支持多轮对话的用户界面
2.2：基于 Luban 框架实现与 KubeSphere 控制台集成
3. 编写完整的项目文档和使用说明书


### 导师联系

- KubeSphere 上海站站长: **张海立**

- 联系邮箱：haili.zhang@outlook.com

### 详细链接

[开源软件供应链点亮计划](https://summer-ospp.ac.cn/org/prodetail/256690088?list=org&navpage=org)
