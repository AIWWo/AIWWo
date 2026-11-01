# Authorization Specification

> **状态**：待完善。核心原则见 ADR-0002、ADR-0003、ADR-0005。

## 1. 目的

定义 Kernel 中授权（Authorization）的模型、流程与策略执行机制。

## 2. 核心原则

- **Kernel 管权限，Provider 管资源**（ADR-0002）。
- **预授权直接执行，遇到边界再申请**（ADR-0003）。
- **能力组合不得提升组成能力的权利**（ADR-0005）。
- 授权判定由代码层面的 Policy Enforcement 完成，不依赖 AI 推理。

## 3. 概念模型

| 概念 | 说明 |
| --- | --- |
| Principal | 执行操作或代表其他主体执行操作的身份 |
| Permission | 能力声明的权限需求 |
| Authorization Grant | 对 Principal 实际授予的权限 |
| Scope | 授权覆盖的资源范围 |
| Constraints | 对授权的附加约束 |
| Permission Budget | 授权的用量预算 |

## 4. 授权流程

```text
Resource Operation
       |
       v
Policy Enforcement
       |
       +-- Authorized (符合 Scope / Constraints / Budget)
       |      |
       |      v
       |    Execute
       |
       +-- Not Authorized
              |
              v
       Is Request Allowed?
          |         |
         Yes        No
          |         |
          v         v
      Request     Deny
      Approval
```

详细说明见 [ADR-0003](../decisions/adr/ADR-0003-preauthorized-execution.md)。

## 5. 待验证问题

- Principal 的完整身份模型是什么？
- 调用链的有效权限如何计算？
- 授权委托和权限继承如何实现？
- 敏感权限如何分级？
- Permission Budget 如何表达？
