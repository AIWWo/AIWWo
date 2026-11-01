# AI Kernel

**Version:** 0.1.0-draft
**Language:** Go（目标技术方向）
**Project Type:** Local AI Infrastructure / AI Capability Runtime

## 项目简介

AI Kernel 是一个面向本地 AI 能力生态的通用运行底座。

它不是一个单纯的 Agent Framework，而是希望建立一套统一的基础设施，让不同来源、不同实现形式的 AI 能力能够被发现、运行、组合、替换、复用、保存、版本化、分享和发布。

开发者可以发布完整的 AI 工具，也可以发布可拆分的基础能力。用户可以组合已有能力，创建自己的能力，并将其进一步固化、修改和分享。

## 核心目标

1. 统一不同 AI 工具和能力的运行机制。
2. 将 Capability 与 Implementation 分离。
3. 支持完整工具与原子能力并存。
4. 支持用户创建和组合 Capability。
5. 支持多来源能力发现和接入。
6. 支持能力依赖快照、版本管理和实现替换。
7. 建立统一的授权、安全与资源访问机制。
8. 支持本地运行和可扩展部署。

## 核心设计原则

- Capability 是一等公民。
- 能力身份不由名称或代码相似度单独决定。
- 能力定义、实例和调用必须分离。
- Runtime 管理生命周期。
- Policy 管理授权。
- Provider 管理具体资源。
- 已授权操作直接执行，遇到权限边界才触发申请。
- 能力组合不能自动提升组成能力的许可权利。
- 默认由用户决定是否安装和扩增能力。

## 文档导航

| 目录 | 说明 |
| --- | --- |
| [PROJECT_VISION.md](./PROJECT_VISION.md) | 项目愿景与核心定位 |
| [architecture/](./architecture/) | 系统应该是什么样子 |
| [specifications/](./specifications/) | 具体协议和规则定义 |
| [decisions/](./decisions/) | 已决定与待决定事项 |
| [research/](./research/) | 外部技术调研与验证 |
| [roadmap/](./roadmap/) | 路线图与开发计划 |

## 状态标记说明

本文档体系使用以下状态标记：

- **已确定（Accepted）**：用户已明确决定，进入正式架构并生成 ADR。
- **待确认（Proposed）**：助手提出但用户尚未接受的方案。
- **待验证（To Be Validated）**：尚未研究验证的技术问题。

## 当前开发状态

项目目前处于架构设计与技术调研准备阶段，尚未进入正式实现。

本文档属于架构讨论稿，不应被视为已经完成技术验证的实现规范。
