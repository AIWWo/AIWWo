# Roadmap

> **状态**：草稿。本文档为 AI Kernel 的高层路线图。

## 阶段一：架构设计与调研（当前）

- 完善 Capability 核心定义与 Descriptor Schema。
- 完善 Runtime、Security、Provider 等模块的架构文档。
- 完成外部技术调研（Go 生态、安全、现有项目）。
- 验证关键技术问题。

## 阶段二：核心原型

- 实现 Capability Definition / Instance / Invocation 的最小原型。
- 实现 Policy Enforcement 的最小检查点。
- 实现 Provider 的最小接入协议。
- 实现本地单进程运行。

## 阶段三：扩展能力

- 实现能力组合与快照。
- 实现多来源能力发现。
- 实现 Plugin / MCP 扩展接入。
- 实现 Observability（Trace / Log）。

## 阶段四：生态与发布

- 建立 Registry 信任机制。
- 支持能力发布与分享。
- 完善权限分级与审批流程。
- 性能与稳定性优化。

## 当前状态

项目目前处于**阶段一**：架构设计与技术调研准备阶段，尚未进入正式实现。
