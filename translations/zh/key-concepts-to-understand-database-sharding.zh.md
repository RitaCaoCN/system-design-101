---
title: "理解数据库分片的关键概念"
description: "通过垂直/水平策略了解数据库分片的关键概念。"
image: "https://assets.bytebytego.com/diagrams/0096-dbshards.png"
createdAt: "2024-03-09"
draft: false
categories:
  - database-and-storage
tags:
  - "Database Sharding"
  - "Database Design"
---

![](https://assets.bytebytego.com/diagrams/0096-dbshards.png)

在这份简明且偏可视化的材料里，我们拆解数据库分区的关键概念，并解释垂直与水平这两种策略。

## 基于范围的分片（Range-Based Sharding）

把数据拆成不同的范围。可以把它想成：按题材把书分别放到不同的书架上。

## 基于键的分片（Key-Based Sharding，外加一点 %3 哈希）

想象每条数据都有唯一的 key，我们再按特定规则把它们分散出去。这就像按花色和点数整理扑克牌。

## 基于目录的分片（Directory-Based Sharding）

目录就像电话簿，帮你快速找到需要的信息。类似地，这种技术用一份目录来高效路由数据。
