# Snapshot Specification

> **状态**：待完善。本文档目前为规范骨架。

## 1. 目的

定义 Snapshot 的数据结构与语义，用于记录能力在某个版本或时间点的依赖和实现状态。

## 2. Snapshot 的作用

- **复现**：在不同环境中重建相同的能力组合。
- **分享**：将能力组合分享给其他用户。
- **版本化**：为能力的某个状态提供不可变记录。
- **回滚**：在实现替换或依赖变更后回退到已知状态。

## 3. 初步数据结构（草案）

```yaml
snapshot:
  snapshot_id: string
  created_at: timestamp
  capability:
    id: string
    version: string
  dependencies:                 # 完整的依赖锁定（类似 lock 文件）
    - capability_id: string
      version: string           # 锁定的精确版本
      implementation:
        type: string
        reference: string
        sha256: string
  evidence?:                    # 当时的能力证据快照
    - ...
```

## 4. 待验证问题

- Snapshot 的完整数据结构与字段？
- 版本兼容与迁移策略？
- 快照的签名与完整性校验？
