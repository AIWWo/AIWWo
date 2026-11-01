# Extension

> **状态**：待完善。本文档目前为架构骨架。

## 1. 定位

负责 Plugin、Workflow、MCP 等扩展机制。

## 2. 扩展类型

### Plugin

用于扩展和分发。**架构边界**：Plugin 与 Workflow 分离。

### Workflow

用于编排多个能力的执行流程。

### MCP（Model Context Protocol）

MCP 是一种接入协议，用于将外部工具和资源接入 Kernel。

**架构边界**：MCP 协议与 Resource 类型分离。MCP Service 是能力来源之一，不直接等于资源类型。

## 3. 与核心模块的关系

- 扩展机制本身不改变 Capability 的核心抽象。
- Plugin、Workflow、MCP 最终都映射到 Capability / Provider 的概念上。
- 扩展能力同样受 Security、Runtime、Lifecycle 等核心模块的约束。

## 4. 待确认问题

- Plugin 的加载、隔离与卸载机制？（待验证）
- Workflow 的表达形式与执行引擎？（待验证）
- MCP 接入的适配层设计？（待验证）
