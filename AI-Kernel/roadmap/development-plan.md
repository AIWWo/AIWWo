# Development Plan

> **状态**：草稿。本文档记录详细的开发计划与任务拆解。

## 近期优先事项

### 1. 完善 Capability 核心定义

- [ ] 确定 Capability Descriptor 的正式 Schema。
- [ ] 定义能力身份模型与 ID 规则。
- [ ] 定义接口兼容性判断规则。

### 2. 完善核心模块架构

- [ ] Runtime：并发策略、状态管理、调用链。
- [ ] Security：Principal 模型、授权流程、Permission Budget。
- [ ] Provider：接入协议、认证、崩溃恢复。
- [ ] Composition：组合规则、快照结构、依赖解析。

### 3. 技术调研

- [ ] Go 生态库选型。
- [ ] 安全模型调研。
- [ ] 现有项目对比。

### 4. 原型验证

- [ ] 最小 Capability 运行原型。
- [ ] Policy Enforcement 检查点原型。
- [ ] Provider 接入原型。

## 任务追踪

详细开放问题见 [decisions/open-questions.md](../decisions/open-questions.md)。
