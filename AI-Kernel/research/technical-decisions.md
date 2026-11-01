# Technical Decisions Research

> **状态**：未开始。本文档用于记录关键技术决策的调研与验证结果。

## 1. 调研目的

对架构中尚未确定的技术方案进行调研和验证，为决策提供依据。

## 2. 待验证技术问题

以下问题来自 [decisions/open-questions.md](../decisions/open-questions.md)：

### Capability Descriptor Schema

- 正式 Schema 结构
- 接口兼容性判断方式
- 版本与依赖冲突管理

### 能力身份

- ID 生成规则
- 来源签名机制
- 多来源证据交叉验证

### 运行时

- 并发策略
- 状态持久化与恢复
- 调用链传播

### 安全

- Principal 身份模型
- 调用链权限计算
- Permission Budget 表达

### Provider

- 进程内 / 进程外支持
- Policy 不可绕过机制
- 崩溃恢复

## 3. 验证方法

（待补充：原型实现、对比实验、性能基准等）

## 4. 结论

（待补充）
