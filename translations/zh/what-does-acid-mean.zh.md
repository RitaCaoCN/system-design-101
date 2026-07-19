---
title: "ACID 是什么意思？"
description: "理解数据库事务中的 ACID 特性。"
image: "https://assets.bytebytego.com/diagrams/0407-what-does-acid-mean.png"
createdAt: "2024-03-12"
draft: false
categories:
  - database-and-storage
tags:
  - "Databases"
  - "ACID"
---

上图解释了在数据库事务语境下，ACID 分别代表什么。

![](https://assets.bytebytego.com/diagrams/0407-what-does-acid-mean.png)

## Atomicity

一个事务中的所有写操作会作为一个整体执行，不能被拆成更小的部分。如果事务执行过程中发生故障，这个事务中的所有写操作都要被回滚。

所以，原子性可以理解为“要么全部成功，要么全部失败”。

## Consistency

这里的“一致性”不同于 CAP 定理中的 consistency。CAP 里的 consistency 指的是每次读取都能拿到最新写入的数据，或者拿到错误；而这里的一致性指的是维护数据库约束和不变量。事务写入的数据必须满足所有已定义规则，并让数据库始终保持在一个有效状态。

## Isolation

当两个不同事务同时写入数据时，它们彼此之间应该相互隔离。最严格的隔离级别是 **serializability（可串行化）**，也就是每个事务看起来都像自己独占整个数据库一样。不过，这种级别在现实里实现成本很高，因此我们通常会采用更低一些的隔离级别。

## Durability

事务一旦提交，即使系统发生故障，数据也必须已经被持久化保存下来。在分布式系统中，这通常还意味着数据会被复制到其他节点。
