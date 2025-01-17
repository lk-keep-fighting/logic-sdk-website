---
sidebar_position: 3
---
# 特性介绍
## 1. 可视化设计与调试
:::tip

通过及时的设计与调试，可极大的提升流程开发效率与体验。

:::
- 设计界面
    <img src="/img/capture/可视化设计.png"/>

- 调试功能
    <img src="/img/capture/可视化调试.png"/>

## 2. 有状态与无状态运行
:::tip

- 无状态是最简单的入参-执行-返回，像一个函数；
- 有状态会传入此流程唯一业务标识进行状态保持，配合*交互点*配置，实现有多次交互的流程执行。

:::

<img src="/img/capture/有状态与无状态.png"/>

## 3. 运行实例回放
:::tip

在有状态的运行时，根据传入的业务标识会产生运行实例，可通过界面跟踪当前状态和历史回放。

:::

<img src="/img/capture/实例回放.png"/>

## 4. 异常重试
通过业务实例在DB缓存的上下文（入参、局部变量、环境变量）进行重试，还原异常发生时的业务状态，恢复业务执行。
- 可视化按钮点击重试
<img src="/img/capture/可视化异常重试.png"/>
- 代码触发重试
```java 
    runnerService.retryErrorBiz("logicId", "bizId");
```