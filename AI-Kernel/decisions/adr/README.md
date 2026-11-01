# Architecture Decision Records (ADR)

本目录记录 AI Kernel 的架构决策。

## 格式

每份 ADR 遵循以下结构：

```
# ADR-XXXX: <标题>

Status: Accepted | Proposed | Superseded
Date: YYYY-MM-DD

## 背景
## 决策
## 理由
## 影响
## 参考
```

## 决策列表

| ADR | 标题 | 状态 |
| --- | --- | --- |
| [ADR-0001](./ADR-0001-capability-first.md) | Capability 是一等公民 | Accepted |
| [ADR-0002](./ADR-0002-resource-provider.md) | Kernel 管权限，Provider 管资源 | Accepted |
| [ADR-0003](./ADR-0003-preauthorized-execution.md) | 预授权直接执行，遇到边界再申请 | Accepted |
| [ADR-0004](./ADR-0004-capability-identity.md) | 能力身份不由系统擅自合并 | Accepted |
| [ADR-0005](./ADR-0005-rights-non-escalation.md) | 能力组合不得提升组成能力权利 | Accepted |

## 状态说明

- **Accepted**：已被用户明确接受的决策。
- **Proposed**：助手提出但尚未被用户接受的决策。
- **Superseded**：被后续决策取代的旧决策（保留记录，不抹除历史）。
