# Lifecycle Specification

> **状态**：待完善。本文档目前为规范骨架。

## 1. 目的

定义 Capability Instance 从创建到销毁的生命周期状态机与转换规则。

## 2. 生命周期阶段（初步）

```text
Created → Initialized → Running → (Paused?) → Stopping → Destroyed
                |              |
                v              v
            Error          Suspended
```

> 以上为初步设想，正式状态机待定义。

## 3. 状态说明

| 状态 | 说明 |
| --- | --- |
| Created | Instance 已创建，尚未初始化 |
| Initialized | 依赖与资源已就绪，可接受调用 |
| Running | 正在处理调用 |
| Error | 发生错误，需恢复或销毁 |
| Suspended | 挂起（可选，待确认） |
| Stopping | 正在停止，清理资源 |
| Destroyed | 已销毁，资源已释放 |

## 4. 渐进固化

用户侧的能力固化流程（见 [02-capability.md](../architecture/02-capability.md) 第 6 节）：

```text
Idea → Temporary Composition → Running Instance → Saved Capability → Versioned Capability → Published Capability
```

## 5. 待验证问题

- Capability Instance 是否支持持久化和重启恢复？
- 状态转换的触发条件与并发安全？
- 错误恢复策略？
