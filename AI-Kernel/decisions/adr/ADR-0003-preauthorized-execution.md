# ADR-0003: Pre-authorized Execution

Status: Accepted
Date: 2026-11-02

## 背景

让 AI 每次执行任务前都阅读权限文档、判断自己是否有权限并主动申请，会增加不必要的复杂性。

权限判定应当由代码层面的 Policy Enforcement 完成，而不是依赖 AI 推理。

## 决策

采用预授权直接执行机制。

当某个 Principal 已经获得对应权限，并且当前操作符合 Scope、Constraints 和 Permission Budget 时，Kernel 直接允许操作。

当操作遇到权限边界时，才触发权限申请流程。

## 执行流程

```text
Resource Operation
       |
       v
Policy Enforcement
       |
       +-- Authorized
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

## AI 的职责

AI 可以：
- 解释权限需求。
- 辅助准备申请。
- 向用户说明风险。

AI 不可以：
- 自行批准申请。
- 修改授权范围。
- 绕过 Policy。
- 将推理结果当作授权。

## 影响

必须确保所有资源操作都有不可绕过的授权检查点。

## 参考

- [architecture/06-security.md](../../architecture/06-security.md)
- [specifications/authorization.md](../../specifications/authorization.md)
