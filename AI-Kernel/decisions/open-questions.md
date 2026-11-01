# Open Questions

本文档记录尚未确定的架构问题。

## 1. Runtime

- 同一个 Capability Instance 是否允许多个 Task 并发？
- 是否由 Capability 自己声明并发策略？
- Global State 与 Instance State 的修改权如何管理？
- Capability Instance 是否支持持久化和重启恢复？
- Task State 是否正式成为第三层状态？

## 2. Invocation

- 是否允许循环调用？
- 如何检测递归调用？
- 如何限制调用深度？
- 子调用失败时如何处理父调用？
- 取消和超时如何传播？

## 3. Capability

- Capability Descriptor 的正式 Schema 是什么？
- 能力接口兼容性如何判断？
- 如何定义最小原子节点？
- 如何管理能力版本和依赖冲突？

## 4. Security

- Principal 的完整身份模型是什么？
- 调用链的有效权限如何计算？
- 授权委托和权限继承如何实现？
- 敏感权限如何分级？
- Permission Budget 如何表达？

## 5. Provider

- Provider 是否同时支持进程内和进程外？
- 如何确保所有资源操作经过 Policy？
- Provider 如何认证调用主体？
- 如何处理 Provider 崩溃和资源释放？

## 6. Storage

- Global State 与 Instance State 如何持久化？
- 是否使用统一存储抽象？
- Memory 与一般 State 如何区分？
- 如何进行数据迁移和版本兼容？

## 7. Ecosystem

- Registry 如何建立信任机制？
- 如何验证能力来源？
- 如何防止评价刷分？
- 如何处理许可证冲突？
