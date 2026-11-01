# Capability

> **状态**：本文档为架构初稿。已确定的设计原则见各 ADR；Capability Descriptor 的正式 Schema 见 [specifications/capability-descriptor.md](../specifications/capability-descriptor.md)。

## 1. 定位

Capability 是 AI Kernel 的一等公民（ADR-0001）。

它是系统中描述、运行、组合、复用、保存、版本化和分享的核心对象。

Capability 不是某一种具体的 Agent、Tool 或 Plugin，而是一个统一的能力抽象。

## 2. Capability 可以是什么

- 一个完整 AI 工具。
- 一个独立基础能力。
- 多个能力的组合。
- 用户临时创建的组合。
- 用户固化后的能力。
- 第三方发布的能力。
- 系统生成的能力。

## 3. 核心对象层次

Capability 在系统中分为三个层次，三者必须分离（架构边界）：

### 3.1 Capability Definition

能力的静态定义。包含：

- 身份（Identity）
- 描述（Description）
- 接口（Interface / Input-Output）
- 版本（Version）
- 依赖（Dependencies）
- 实现引用（Implementation Reference）

详细字段由 [Capability Descriptor](../specifications/capability-descriptor.md) 定义。

### 3.2 Capability Instance

Capability Definition 的运行实例。

- 一个 Definition 可以创建多个 Instance。
- Instance 拥有自身的运行状态和资源句柄。
- Instance 由 Runtime 负责生命周期管理。

### 3.3 Invocation

对某个 Capability Instance 或能力入口的一次具体调用。

- 一次调用有独立的输入、输出、上下文和执行记录。
- Invocation 之间可以形成动态父子调用关系。
- 调用链的权限计算遵循 Security 模块规则。

## 4. 能力身份

**已确定（ADR-0004）**：能力身份不由系统擅自合并。

能力身份不由名称或代码相似度单独决定。系统不得因为两个能力名称相似或实现相近就自动将其视为同一能力。

能力身份的确定需要明确的、可追溯的依据（例如显式的 ID、来源签名、版本链等）。具体身份模型见 [05-identity-discovery.md](./05-identity-discovery.md)。

## 5. 能力与实现分离

**已确定（架构边界）**：Capability 与 Implementation 分离。

- Capability Definition 描述"能力是什么"和"需要什么"。
- Implementation 描述"能力如何实现"。
- 同一 Capability 可以有多个实现，用户或系统可以在兼容前提下替换实现。
- 实现替换的兼容性判断依据为接口契约，而非实现细节。

## 6. 渐进固化生命周期

用户可以从临时组合开始，逐步将能力固化：

```text
Idea → Temporary Composition → Running Instance → Saved Capability → Versioned Capability → Published Capability
```

每个阶段的状态转换规则由 Runtime 与 Lifecycle 规范定义。用户创造的能力可以继续被修改、组合和发布。

## 7. 能力组合

**已确定（ADR-0005）**：能力组合不得提升组成能力的权利。

当多个 Capability 组合成一个新的 Capability 时：

- 新能力的权限范围是其组成能力权限的**交集或子集**，不得自动扩展。
- 组合能力对外暴露的接口由组合定义显式声明。
- 组合能力不能绕过组成能力各自的授权检查。

详细组合机制见 [04-composition.md](./04-composition.md)。

## 8. 依赖与快照

- Capability 可以声明对其他 Capability 的依赖。
- Snapshot 记录能力在某个版本或时间点的依赖和实现状态。
- 快照使得能力可以被复现、分享和在不同环境中重建。

详见 [04-composition.md](./04-composition.md) 与 [specifications/snapshot.md](../specifications/snapshot.md)。

## 9. 来源

Capability 可以来自多种来源（详见 PROJECT_VISION 第 5 节）：

- 官方 / 第三方 / 社区 Registry
- Git
- 本地文件系统
- 本地进程
- Remote API
- MCP Service
- 现有 AI 工具
- 用户创建的能力

Registry 只是来源，不是能力本身。来源接入与发现机制见 [05-identity-discovery.md](./05-identity-discovery.md)。

## 10. 待确认与待验证问题

以下问题尚未确定，记录于 [decisions/open-questions.md](../decisions/open-questions.md)：

- Capability Descriptor 的正式 Schema 是什么？（待验证）
- 能力接口兼容性如何判断？（待验证）
- 如何定义最小原子节点？（待确认）
- 如何管理能力版本和依赖冲突？（待验证）
