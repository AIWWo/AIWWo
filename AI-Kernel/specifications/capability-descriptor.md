# Capability Descriptor

> **状态**：待验证。本文档定义 Capability Descriptor 的初始 Schema 草案，尚未经过技术验证。

## 1. 目的

Capability Descriptor 是 Capability Definition 的结构化描述，用于声明能力的身份、接口、依赖和实现引用。

它是能力发现、组合、版本管理和实现替换的基础。

## 2. 设计原则

- **身份优先**：Descriptor 必须包含明确的能力身份，且身份不由名称或代码相似度决定。
- **接口契约**：通过接口声明实现兼容性判断的依据。
- **实现解耦**：Definition 与 Implementation 分离，Descriptor 引用实现而不内嵌实现。
- **可组合**：Descriptor 支持声明对其他 Capability 的依赖。

## 3. Schema 草案

以下为初始草案，字段与类型均待验证。

```yaml
# Capability Descriptor Schema (Draft)
capability:
  # --- 身份 ---
  id: string                      # 全局唯一能力 ID（待验证：ID 生成规则）
  name: string                    # 人类可读名称
  version: string                 # 语义化版本号
  description: string             # 能力描述

  # --- 发布者 ---
  publisher:                      # 发布者身份（待验证：信任模型）
    id: string
    name: string
    signature?: string            # 发布者签名

  # --- 接口契约 ---
  interface:
    inputs:                       # 输入参数声明
      - name: string
        type: string              # 待验证：类型系统
        required: boolean
        description?: string
    outputs:                      # 输出声明
      - name: string
        type: string
        description?: string
    errors:                       # 可能的错误
      - code: string
        description?: string

  # --- 权限需求 ---
  permissions:                    # 能力声明所需的权限（Permission）
    - action: string
      scope: string
      constraints?:               # 约束
        max_count?: number
        time_window?: string
        data_sensitivity?: string

  # --- 依赖 ---
  dependencies:                   # 对其他 Capability 的依赖
    - capability_id: string
      version_range: string       # 兼容的版本范围
      interface_constraint?: string  # 接口兼容性约束

  # --- 实现引用 ---
  implementation:
    type: string                  # local_process | remote_api | mcp | plugin | ...
    reference: string             # 实现的定位信息
    sha256?: string               # 实现内容哈希（待验证：完整性校验）

  # --- 来源与证据 ---
  sources:                        # 能力来源列表
    - type: string                # registry | git | local | ...
      uri: string
  evidence?:                      # 多来源证据（Capability Evidence）
    - type: string
    uri: string
    signature?: string

  # --- 元数据 ---
  metadata:
    created_at: timestamp
    updated_at: timestamp
    license?: string
    tags?: [string]
```

## 4. 身份字段说明

`id` 是能力的核心身份标识。根据 ADR-0004，能力身份不由名称或代码相似度决定，因此 `id` 必须具有全局唯一性和不可篡改性。

**待验证**：ID 的具体生成规则（例如基于内容哈希、发布者命名空间 + 随机 ID、或去中心化标识）。

## 5. 接口兼容性

实现替换的兼容性判断基于 `interface` 字段：

- 输入参数：新实现必须接受旧接口的所有必填输入。
- 输出：新实现必须提供旧接口声明的所有输出。
- 错误：新实现应覆盖旧接口声明的错误集合。

**待验证**：兼容性判断的严格程度（结构兼容 vs. 语义兼容）。

## 6. 与权限的关系

`permissions` 字段声明能力运行所需的权限（Permission）。

注意区分：

- **Permission**：能力声明的需求。
- **Authorization Grant**：实际授予的权限，由 Security 模块管理。

权限授予遵循 ADR-0003（预授权直接执行）和 ADR-0005（组合不提升权利）。

## 7. 开放问题

- Capability Descriptor 的正式 Schema 是什么？（待验证）
- 能力接口兼容性如何判断？（待验证）
- 如何管理能力版本和依赖冲突？（待验证）
- 身份 ID 的生成与全局唯一性保证？（待验证）
- 发布者签名与信任机制？（待验证）
