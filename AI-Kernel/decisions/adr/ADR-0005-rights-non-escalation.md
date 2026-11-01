# ADR-0005: 能力组合不得提升组成能力权利

Status: Accepted
Date: 2026-11-02

## 背景

当多个 Capability 组合成一个新的 Capability 时，如果允许新能力自动获得超出组成能力的权限，会导致权限膨胀：

- 组合能力可能获得其组成能力都不具备的权限。
- 攻击者可能通过组合来绕过单个能力的权限限制。
- 用户难以理解组合能力的实际权限范围。

## 决策

能力组合不得提升组成能力的权利。

当多个 Capability 组合成一个新的 Capability 时，新能力的权限范围是其组成能力权限的**交集或子集**，不得自动扩展。

## 理由

- 最小权限原则：组合能力不应获得超出其组成部分的权限。
- 安全可预测：用户可以通过组成能力的权限推知组合能力的权限上限。
- 防止绕过：不能通过组合来规避单个能力的授权限制。

## 影响

- 组合能力的权限必须显式计算为组成能力权限的交集或子集。
- 组合能力对外暴露的接口由组合定义显式声明，不得隐式扩展。
- 组合能力不能绕过组成能力各自的授权检查。

## 参考

- [architecture/04-composition.md](../../architecture/04-composition.md)
- [architecture/11-rights-distribution.md](../../architecture/11-rights-distribution.md)
- [specifications/authorization.md](../../specifications/authorization.md)
