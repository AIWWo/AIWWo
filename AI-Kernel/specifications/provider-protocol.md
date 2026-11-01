# Provider Protocol

> **状态**：待完善。核心边界见 ADR-0002。

## 1. 目的

定义 Provider 接入 Kernel 的统一协议，包括能力声明、操作接口、身份认证与资源释放。

## 2. 核心原则

- **Kernel 管权限，Provider 管资源**（ADR-0002）。
- 所有资源操作必须经过 Kernel 的 Policy Enforcement。
- Provider 必须认证调用主体（Principal）。
- Provider 崩溃时的资源释放必须有保障。

## 3. Provider 类型

- File Provider
- Model Provider
- Network Provider
- 其他（数据库、本地进程、Remote API、MCP Service 等）

## 4. 协议要素

### 资源能力声明

Provider 声明自身能提供的资源类型与操作。

### 操作接口

对资源执行的动作（Action）及其输入输出。

### 调用主体认证

Provider 如何确认调用者的 Principal 身份。

### 错误与资源释放

- 错误报告格式。
- Provider 异常退出时的资源清理机制。

## 5. 待验证问题

- Provider 是否同时支持进程内和进程外？
- 如何确保所有资源操作经过 Policy？
- Provider 如何认证调用主体？
- 如何处理 Provider 崩溃和资源释放？
