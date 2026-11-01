# AI Kernel Architecture Overview

## 1. 总体架构

AI Kernel 由多个相互协作的基础模块组成。

```text
                 User / Client
                       |
                       v
                  Gateway
                       |
                       v
                 Kernel Runtime
                       |
       +---------------+---------------+
       |               |               |
   Capability       Security       Lifecycle
       |               |               |
       +---------------+---------------+
                       |
                       v
                Invocation Engine
                       |
                       v
               Provider / Executor
                       |
          +------------+------------+
          |            |            |
      File Provider Model Provider Network Provider
          |            |            |
          +------------+------------+
                       |
                       v
                External Resources
```

## 2. 核心模块职责

### Kernel

负责基础运行环境、身份、上下文、生命周期和模块协调。

### Capability

负责能力定义、身份、版本、组合和能力描述。

### Runtime

负责实例化、调用、并发、取消、超时和资源清理。

### Security

负责 Principal、Authorization Grant、Scope、Constraints 和 Policy Enforcement。

### Provider

负责具体资源和外部服务的访问。

### Composition

负责能力组合、依赖解析、快照和替换实现。

### Discovery

负责能力来源接入、搜索、比较、验证和推荐。

### Extension

负责 Plugin、Workflow、MCP 等扩展机制。

### Observability

负责 Trace、Log、Replay 和运行状态观察。

## 3. 核心架构原则

Runtime 管生命周期。

Policy 管能不能做。

Provider 管具体资源操作。

Sandbox 管执行影响范围。

Trace 管发生了什么。

Composition 管能力如何组合。

Plugin 管扩展和分发。

Capability 是整个系统的核心能力对象。

## 4. 架构边界

Resource 与 Kernel 分离。

Capability 与 Implementation 分离。

Definition 与 Instance 分离。

Instance 与 Invocation 分离。

Event 与 Command 分离。

Permission 与 Authorization Grant 分离。

MCP 协议与 Resource 类型分离。

Plugin 与 Workflow 分离。

## 5. 当前状态

这是逻辑架构，不代表最终 Go Package、进程部署或接口结构。
