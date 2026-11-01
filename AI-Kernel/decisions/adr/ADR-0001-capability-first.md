# ADR-0001: Capability 是一等公民

Status: Accepted
Date: 2026-11-02

## 背景

当前 AI 工具生态中，不同系统围绕各自的 Agent、Tool 或 Plugin 概念构建，导致能力身份、运行协议和复用机制互不兼容。用户为了使用不同工具的优势，往往需要部署多个完整系统，造成重复建设和能力孤岛。

## 决策

将 Capability 作为 AI Kernel 的一等公民（First-class Citizen）。

系统围绕 Capability 建立，而不是围绕某一种 Agent、Tool 或 Plugin 建立。所有核心机制——发现、运行、组合、替换、复用、保存、版本化、分享、发布——都以 Capability 为中心对象。

## 理由

- 统一抽象：Capability 可以表达完整工具、原子能力、组合能力等多种形态。
- 解耦实现：Capability 与 Implementation 分离，使能力可以被替换和复用。
- 用户中心：用户可以像组合软件组件一样组合 AI 能力。

## 影响

- 所有模块的设计都需要以 Capability 为核心对象。
- Capability 的定义、身份、接口和生命周期必须优先稳定。
- 后续 Runtime、Plugin、Workflow、Registry 等模块都建立在 Capability 抽象之上。

## 参考

- [architecture/02-capability.md](../../architecture/02-capability.md)
- [PROJECT_VISION.md](../../PROJECT_VISION.md)
