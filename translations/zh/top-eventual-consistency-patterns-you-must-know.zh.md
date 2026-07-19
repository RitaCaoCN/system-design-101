---
title: "必须知道的最终一致性模式"
description: "了解分布式数据库设计中的最终一致性模式。"
image: "https://assets.bytebytego.com/diagrams/0100-eventual-consistency-patterns-you-must-know.png"
createdAt: "2024-02-15"
draft: false
categories:
  - database-and-storage
tags:
  - "Consistency"
  - "Databases"
---

![](https://assets.bytebytego.com/diagrams/0100-eventual-consistency-patterns-you-must-know.png)

最终一致性是一种数据一致性模型，它确保分布式数据库上的更新最终会反映到所有节点上。像异步复制这样的技术，可以帮助实现最终一致性。

不过，最终一致性也可能带来数据不一致。下面是 4 种可以帮助你设计应用的模式。

## 基于事件的最终一致性

服务发出事件，其他服务监听这些事件，并更新各自的数据库实例。这样服务之间耦合更松，但数据达到一致会有延迟。

## 基于后台同步的最终一致性

在这种模式中，后台任务负责让多个数据库中的数据保持一致。因为后台任务按固定计划运行，所以最终一致性的到达速度会更慢。

## 基于 Saga 的最终一致性

Saga 是一系列本地事务组成的流程，每个事务只更新一个服务的数据。它用于管理长生命周期、最终一致的事务。

## 基于 CQRS 的最终一致性

把读操作和写操作拆分到不同的数据库中，让它们最终保持一致。读模型和写模型可以分别针对不同需求进行优化。
