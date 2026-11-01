# AI Kernel — Project Vision

## 1. 项目愿景

建立一个类似操作系统内核的本地 AI 基础设施。

不同 AI 工具可以在这个底座上提供能力，而不必各自重复实现完整的运行环境、权限控制、资源管理和扩展机制。

用户可以像组合软件组件一样组合 AI 能力。

## 2. 核心问题

当前不同 AI 工具往往拥有自己的：

- Memory 系统
- Plugin 系统
- Permission 系统
- Agent Runtime
- Workflow
- Model Provider
- Tool Calling
- 数据存储

不同工具之间缺少统一的能力身份、运行协议和复用机制。

这导致用户为了使用不同工具的优势，往往需要部署多个完整系统。

AI Kernel 希望解决这种重复建设和能力孤岛问题。

## 3. Capability-first

系统围绕 Capability 建立，而不是围绕某一种 Agent、Tool 或 Plugin 建立。

Capability 可以是：

- 一个完整 AI 工具。
- 一个独立基础能力。
- 多个能力的组合。
- 用户临时创建的组合。
- 用户固化后的能力。
- 第三方发布的能力。
- 系统生成的能力。

## 4. 渐进固化

用户可以从临时组合开始：

Idea → Temporary Composition → Running Instance → Saved Capability → Versioned Capability → Published Capability

用户创造的能力可以继续被修改、组合和发布。

## 5. 开放生态

能力可以来自：

- 官方 Registry
- 第三方 Registry
- 社区 Registry
- Git
- 本地文件系统
- 本地进程
- Remote API
- MCP Service
- 现有 AI 工具
- 用户创建的能力

Registry 只是来源，不是能力本身。

## 6. 用户自主权

默认情况下：

系统发现、分析、比较、验证和推荐，用户决定是否采用。

只有用户明确授权自主扩增后，系统才可以在授权范围内自行获取和安装新能力。

涉及敏感权限时，仍然必须遵守独立审批规则。

## 7. 重要设计理念

AI Kernel 不应预先规定开发者只能创造什么。

它应该定义统一的能力描述、接入、调用、安全和生命周期规则，让生态能够自然扩展。
