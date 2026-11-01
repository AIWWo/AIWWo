# State & Memory

> **状态**：待完善。本文档目前为架构骨架。

## 1. 定位

负责系统中各类状态与记忆的管理、持久化与隔离。

## 2. 状态层次

系统中可能存在以下状态层次：

### Global State

整个 Kernel 范围的全局状态。修改权需要严格管理。

### Instance State

每个 Capability Instance 自身的运行状态。

### Task State

单次调用（Invocation / Task）的状态。是否正式成为第三层状态仍待确认。

### Memory

AI 相关的记忆数据。Memory 与一般 State 需要区分（见开放问题）。

## 3. 关键问题

- Global State 与 Instance State 的修改权如何管理？（待验证）
- Capability Instance 是否支持持久化和重启恢复？（待确认）
- Task State 是否正式成为第三层状态？（待确认）
- Memory 与一般 State 如何区分？（待验证）
- 如何进行数据迁移和版本兼容？（待验证）

## 4. 与其他模块的关系

| 模块 | 关系 |
| --- | --- |
| Runtime | Runtime 读写 Instance State 与 Invocation Context |
| Security | 状态访问受授权约束 |
| Composition | Snapshot 依赖状态记录 |
| Observability | Trace 记录状态变化 |

## 5. 待确认与待验证问题

记录于 [decisions/open-questions.md](../decisions/open-questions.md) Storage 部分：

- Global State 与 Instance State 如何持久化？（待验证）
- 是否使用统一存储抽象？（待确认）
- Memory 与一般 State 如何区分？（待验证）
- 如何进行数据迁移和版本兼容？（待验证）
