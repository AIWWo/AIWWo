# Security

> **状态**：待完善。核心原则已确定（见 ADR-0002、ADR-0003、ADR-0005），详细模型待定义。

## 1. 定位

Security 负责 Principal、Authorization Grant、Scope、Constraints 和 Policy Enforcement。

**核心架构原则**：Policy 管能不能做。

## 2. 核心概念

### Principal

执行操作或代表其他主体执行操作的身份。完整身份模型待定义。

### Authorization Grant

对 Principal 授予特定动作（Action）、资源范围（Scope）和约束（Constraints）的授权。

**架构边界**：Permission 与 Authorization Grant 分离。Permission 是能力声明的需求，Authorization Grant 是实际授予的权限。

### Scope & Constraints

- Scope：授权覆盖的资源范围。
- Constraints：对授权的附加约束（例如调用次数、时间窗口、数据敏感度限制）。

### Permission Budget

**已确定（ADR-0003 相关）**：授权判断必须考虑 Permission Budget。当操作符合已授予的 Scope、Constraints 和 Permission Budget 时直接执行。

## 3. 预授权直接执行机制

**已确定（ADR-0003）**：采用预授权直接执行。

- 已授权操作：Kernel 直接允许执行，不依赖 AI 推理判断权限。
- 遇到权限边界：触发权限申请流程。
- AI 可以解释权限需求、辅助准备申请、说明风险，但不得自行批准、修改授权范围或绕过 Policy。

详细流程见 [ADR-0003](../decisions/adr/ADR-0003-preauthorized-execution.md)。

## 4. Policy Enforcement

所有资源操作必须经过不可绕过的授权检查点。

- 检查点位于 Kernel 与 Provider 之间。
- Provider 不得直接被外部调用，必须经过 Kernel 的 Policy Enforcement。
- 授权判定由代码层面完成，不依赖 AI 推理。

## 5. 调用链权限

当 Capability 调用其他 Capability 时：

- 子调用的有效权限如何计算？（待验证）
- 授权委托和权限继承如何实现？（待验证）
- 敏感权限如何分级？（待验证）

## 6. 待确认与待验证问题

记录于 [decisions/open-questions.md](../decisions/open-questions.md) Security 部分：

- Principal 的完整身份模型是什么？（待验证）
- 调用链的有效权限如何计算？（待验证）
- 授权委托和权限继承如何实现？（待验证）
- 敏感权限如何分级？（待验证）
- Permission Budget 如何表达？（待验证）
