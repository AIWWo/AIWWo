# ADR-0002: Kernel 管权限，Provider 管资源

Status: Accepted
Date: 2026-11-02

## 背景

在 AI 系统中，权限控制与资源访问经常耦合在一起。如果资源提供方（Provider）自行决定权限，会导致权限策略分散、难以统一审计，且存在绕过风险。

## 决策

采用 **Kernel 管权限，Provider 管资源** 的职责分离。

- **Kernel** 负责授权（Authorization）与策略执行（Policy Enforcement）。
- **Provider** 负责具体资源和外部服务的访问。
- 所有资源操作必须经过 Kernel 的授权检查点，Provider 不得被外部直接调用。

## 理由

- 集中授权：权限策略在 Kernel 层统一执行，便于审计和保证一致性。
- 不可绕过：资源操作必须经过检查点，防止 Provider 自行放行。
- 可替换：Provider 只关注资源实现，权限逻辑集中在 Kernel，便于替换 Provider。

## 影响

- Provider 必须实现与 Kernel 的授权检查集成。
- 必须确保所有资源操作都有不可绕过的授权检查点。
- Provider 需要认证调用主体（Principal），但授权决策由 Kernel 做出。

## 参考

- [architecture/06-security.md](../../architecture/06-security.md)
- [architecture/07-resource-provider.md](../../architecture/07-resource-provider.md)
- [specifications/authorization.md](../../specifications/authorization.md)
- [specifications/provider-protocol.md](../../specifications/provider-protocol.md)
