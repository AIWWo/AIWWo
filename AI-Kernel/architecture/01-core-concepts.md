# Core Concepts

## 1. Capability

表达用户可以使用的一种 AI 能力。

Capability 是系统的一等公民。

## 2. Capability Definition

描述能力是什么，包括身份、描述、接口、版本、依赖和实现引用。

## 3. Capability Instance

Capability Definition 的运行实例。

一个 Definition 可以创建多个 Instance。

## 4. Invocation

对某个 Capability Instance 或能力入口的一次具体调用。

Invocation 之间可以形成动态父子调用关系。

## 5. Task

代表一项具体任务。

Task 不等同于 Task Context，也不等同于 Capability Instance。

## 6. Provider

提供实际资源或外部服务访问能力的实现层。

## 7. Principal

执行操作或代表其他主体执行操作的身份。

## 8. Authorization Grant

对 Principal 授予特定动作、资源范围和约束的授权。

## 9. Composition

多个 Capability 或实现材料组成的能力结构。

## 10. Snapshot

记录能力在某个版本或时间点的依赖和实现状态。

## 11. Capability Evidence

用于判断能力质量、可信度和兼容性的多来源证据。

## 12. 核心关系

```text
Capability Definition
          |
          v
    Capability Instance
          |
          v
      Invocation
          |
          v
         Task
```

以上为概念关系示意，具体对象引用和生命周期仍需进一步设计。
