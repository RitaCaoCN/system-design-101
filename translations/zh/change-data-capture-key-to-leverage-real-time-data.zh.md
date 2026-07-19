---
title: "变更数据捕获：利用实时数据的关键"
description: "了解变更数据捕获（CDC）如何帮助利用实时数据。"
image: "https://assets.bytebytego.com/diagrams/0133-change-data-capture-key-to-leverage-real-time-data.png"
createdAt: "2024-02-11"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Streaming"
  - "Data Synchronization"
---

![](https://assets.bytebytego.com/diagrams/0133-change-data-capture-key-to-leverage-real-time-data.png)

世界上 90% 的数据是在过去两年里产生的，而且这种增长只会更快。

不过，最大的挑战是如何实时利用这些数据。数据在不断变化，会让数据库、数据湖和数据仓库彼此失去同步。

CDC，也就是 Change Data Capture（变更数据捕获），可以帮助你应对这个挑战。

CDC 会识别并捕获数据库中的数据变更，让你能把这些变更复制并同步到多个系统。

## 变更数据捕获如何工作

那么，变更数据捕获是怎么工作的呢？下面按步骤拆解：

1. 数据修改：源数据库中的数据发生变更。可能是对某张表的插入、更新或删除操作。

2. 变更捕获：CDC 工具监控数据库事务日志，捕获这些修改。它通过 source connector 连接数据库并读取日志。

3. 变更处理：把捕获到的变更进行处理和转换，变成适合下游系统的格式。

4. 变更传播：处理后的变更会发布到消息队列，再传播到目标系统，例如数据仓库、分析平台、像 Redis 这样的分布式缓存等。

5. 实时集成：CDC 工具用 sink connector 消费日志并更新目标系统。变更会实时到达，从而支持无冲突的数据分析和决策。

用户只需要关心第 1 步，其他步骤都是透明的。

一个流行的 CDC 方案是把 Debezium 和 Kafka Connect 搭配使用，以 Kafka 作为 broker，把数据变更从源系统流式同步到目标系统。Debezium 为大多数数据库都提供了 connector，例如 MySQL、PostgreSQL、Oracle 等。
