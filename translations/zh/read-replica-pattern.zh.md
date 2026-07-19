---
title: "读副本模式"
description: "了解数据库设计与优化中常见的读副本模式。"
image: "https://assets.bytebytego.com/diagrams/0312-read-replica-pattern.png"
createdAt: "2024-01-28"
draft: false
categories:
  - database-and-storage
tags:
  - "Database Replication"
  - "Read Scalability"
---

![](https://assets.bytebytego.com/diagrams/0312-read-replica-pattern.png)

这篇文章介绍一种简单但非常常见的数据库设计模式：**读副本模式**。

在这种架构里，所有会修改数据的操作，例如 `insert`、`delete`、`update`，都会发送到主库，而读请求则发送到读副本。

上图展示了这个流程：

1. 当 Alice 在 amazon.com 下单时，请求会被发送到订单服务。
2. 订单服务会在主库中写入一条订单记录。随后数据会复制到两个副本中。
3. Alice 查看订单详情时，数据由某个副本返回。
4. Alice 查看最近订单历史时，数据同样由某个副本返回。

这种架构有一个主要问题：**复制延迟**。

在某些情况下，例如网络延迟、服务器过载等，副本中的数据可能会落后主库几秒，甚至几分钟。此时，如果 Alice 在下单后立刻查询订单状态，而这个查询恰好由副本处理，那么她可能根本看不到刚下的订单，这会让人感到困惑。这种情况下，我们需要“写后读一致性（read-after-write consistency）”。

## 缓解这个问题的几种办法

* 对延迟敏感的读取请求直接发送到主库。

* 写操作之后紧跟着发生的读取请求路由到主库。

* 关系型数据库通常会提供某种方式来判断副本是否已经追上主库。如果数据已是最新，就查询副本；否则让读取失败，或者改为从主库读取。
