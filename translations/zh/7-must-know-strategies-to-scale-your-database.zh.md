---
title: "扩展数据库的 7 个必知策略"
description: "了解 7 种有效扩展数据库的关键策略。"
image: "https://assets.bytebytego.com/diagrams/0161-database-scaling-cheatsheet.png"
createdAt: "2024-03-15"
draft: false
categories:
  - database-and-storage
tags:
  - "database scaling"
  - "database optimization"
---

![](https://assets.bytebytego.com/diagrams/0161-database-scaling-cheatsheet.png)

## 1. 索引

检查应用的查询模式，并建立合适的索引。

## 2. 物化视图

预先计算复杂查询的结果，并把结果保存下来，以便更快访问。

## 3. 反规范化

通过减少复杂 Join 来提升查询性能。

## 4. 垂直扩展

通过增加更多 CPU、RAM 或存储，来增强数据库服务器能力。

## 5. 缓存

把频繁访问的数据存放在更快的存储层中，以减轻数据库负载。

## 6. 复制

在不同服务器上为主数据库创建副本，用于扩展读能力。

## 7. 分片

把数据库表拆成更小的部分，并分布到多台服务器上。这既可以扩展写能力，也可以扩展读能力。
