# Observability

> **状态**：待完善。本文档目前为架构骨架。

## 1. 定位

负责 Trace、Log、Replay 和运行状态观察。

**核心架构原则**：Trace 管发生了什么。

## 2. 能力范围

### Trace

记录能力调用链的完整执行轨迹，包括父子调用关系、输入输出、耗时、错误等。

### Log

系统运行日志，按级别和模块分类。

### Replay

基于 Trace 记录重现历史调用，用于调试、审计和验证。

### 运行状态观察

实时观察 Instance、Invocation、Provider 的运行状态。

## 3. 与其他模块的关系

- Trace 贯穿 Capability → Instance → Invocation 的完整链路。
- Observability 不直接参与执行决策，仅记录和观察。
- 安全相关的操作必须被 Trace 完整记录，用于审计。

## 4. 待确认问题

- Trace 的数据结构与存储方式？（待验证）
- Replay 的隔离机制（避免重放产生副作用）？（待验证）
- 日志与追踪的采样策略？（待验证）
