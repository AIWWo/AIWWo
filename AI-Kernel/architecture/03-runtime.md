# Runtime

> **状态**：待完善。本文档目前为架构骨架，具体接口与实现尚未定义。

## 1. 定位

Runtime 负责 Capability Instance 的实例化、调用、并发、取消、超时和资源清理。

**核心架构原则**：Runtime 管生命周期。

## 2. 职责范围

- Capability Definition → Capability Instance 的实例化。
- Invocation 的调度与执行。
- 并发控制（同一 Instance 上多个调用的并发策略）。
- 取消（Cancellation）与超时（Timeout）的传播。
- 资源清理与 Instance 销毁。
- Instance 状态的读写与持久化协调。

## 3. 与其他模块的关系

| 模块 | 关系 |
| --- | --- |
| Capability | Runtime 消费 Capability Definition，创建和管理 Instance |
| Security | Runtime 在执行前后触发 Policy Enforcement |
| Lifecycle | Runtime 实现生命周期状态机 |
| Invocation Engine | Runtime 调度具体的调用执行 |
| Provider | Runtime 通过 Provider 访问外部资源 |

## 4. 关键概念

### Capability Instance State

Instance 在运行过程中拥有自身状态。状态修改权需要明确管理（见开放问题）。

### Invocation Context

每次调用携带独立的上下文，包括调用者身份、权限、输入、追踪 ID 等。

### Lifecycle State Machine

Instance 从创建到销毁的状态转换规则，由 [specifications/lifecycle.md](../specifications/lifecycle.md) 定义。

## 5. 待确认与待验证问题

记录于 [decisions/open-questions.md](../decisions/open-questions.md) Runtime 部分：

- 同一个 Capability Instance 是否允许多个 Task 并发？（待确认）
- 是否由 Capability 自己声明并发策略？（待确认）
- Global State 与 Instance State 的修改权如何管理？（待验证）
- Capability Instance 是否支持持久化和重启恢复？（待确认）
- Task State 是否正式成为第三层状态？（待确认）
