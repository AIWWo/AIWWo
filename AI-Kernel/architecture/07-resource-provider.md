# Resource Provider

> **状态**：待完善。核心边界已确定（ADR-0002），详细协议待定义。

## 1. 定位

Provider 提供实际资源或外部服务访问能力的实现层。

**核心架构原则**：Provider 管具体资源操作。
**已确定（ADR-0002）**：Kernel 管权限，Provider 管资源。

## 2. 架构边界

- **Resource 与 Kernel 分离**：资源访问由 Provider 实现，Kernel 不直接操作资源。
- **所有资源操作必须经过 Policy**：Provider 必须通过 Kernel 的授权检查点。
- **MCP 协议与 Resource 类型分离**：MCP 是接入协议之一，不直接等于资源类型。

## 3. Provider 类型

- File Provider：文件系统资源。
- Model Provider：AI 模型推理资源。
- Network Provider：网络访问资源。
- 其他：数据库、本地进程、Remote API、MCP Service 等。

## 4. Provider 协议

Provider 需要实现统一的接入协议，包括：

- 资源能力声明（Provider 能提供什么）。
- 操作接口（对资源执行的动作）。
- 调用主体认证（Provider 如何确认调用者身份）。
- 错误与资源释放协议。

详细规范见 [specifications/provider-protocol.md](../specifications/provider-protocol.md)。

## 5. 安全约束

- Provider 不得绕过 Kernel 的 Policy Enforcement。
- Provider 必须认证调用主体（Principal）。
- Provider 崩溃时的资源释放必须有保障机制。

## 6. 待确认与待验证问题

记录于 [decisions/open-questions.md](../decisions/open-questions.md) Provider 部分：

- Provider 是否同时支持进程内和进程外？（待确认）
- 如何确保所有资源操作经过 Policy？（待验证）
- Provider 如何认证调用主体？（待验证）
- 如何处理 Provider 崩溃和资源释放？（待验证）
