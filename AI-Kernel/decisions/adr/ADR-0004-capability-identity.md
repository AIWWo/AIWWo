# ADR-0004: 能力身份不由系统擅自合并

Status: Accepted
Date: 2026-11-02

## 背景

在能力生态中，可能存在名称相似、功能相近或实现代码相似的能力。如果系统仅凭名称或代码相似度就自动将这些能力合并为同一能力，可能导致：

- 错误地将不同能力视为同一能力，引发组合与依赖错误。
- 掩盖能力来源与发布者的差异，带来信任与安全风险。
- 破坏能力身份的可追溯性。

## 决策

能力身份不由系统擅自合并。

能力身份不由名称或代码相似度单独决定。系统不得因为两个能力名称相似或实现相近就自动将其视为同一能力。能力身份的确定需要明确的、可追溯的依据（例如显式的 ID、来源签名、版本链等）。

## 理由

- 身份确定性：能力身份必须有明确依据，不能依赖模糊的相似度判断。
- 安全与信任：来源与发布者是能力身份的重要组成部分，不能被自动合并抹除。
- 可追溯：能力的版本演进和来源必须可追溯。

## 影响

- Capability Descriptor 必须包含明确的身份字段（ID）。
- 身份模型需要支持来源签名、版本链等可追溯依据。
- 能力发现与比较时，系统只能推荐候选，合并与否由用户或明确规则决定。

## 参考

- [architecture/02-capability.md](../../architecture/02-capability.md)
- [architecture/05-identity-discovery.md](../../architecture/05-identity-discovery.md)
- [specifications/capability-descriptor.md](../../specifications/capability-descriptor.md)
