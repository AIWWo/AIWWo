# Invocation Specification

> **状态**：待完善。本文档目前为规范骨架。

## 1. 目的

定义对 Capability Instance 或能力入口进行调用（Invocation）的协议与规则。

## 2. 核心概念

- **Invocation**：一次具体调用，携带输入、上下文和调用者身份。
- **调用链**：Invocation 之间可以形成动态父子调用关系。
- **Invocation Context**：调用上下文，包括调用者 Principal、权限、追踪 ID 等。

## 3. 调用流程

1. 调用方发起 Invocation，指定目标 Capability Instance / 入口与输入。
2. Kernel 进行 Policy Enforcement（授权检查）。
3. 授权通过后，Runtime 调度执行。
4. 执行过程中可能产生子调用（形成调用链）。
5. 返回输出或错误。
6. 记录 Trace。

## 4. 待验证问题

- 是否允许循环调用？
- 如何检测递归调用？
- 如何限制调用深度？
- 子调用失败时如何处理父调用？
- 取消和超时如何传播？
