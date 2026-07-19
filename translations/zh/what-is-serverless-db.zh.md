---
title: "什么是 Serverless DB？"
description: "了解无服务器数据库、它们的好处以及与传统云数据库的区别。"
image: "https://assets.bytebytego.com/diagrams/0329-serverlessdb.jpeg"
createdAt: "2024-02-24"
draft: false
categories:
  - database-and-storage
tags:
  - "Serverless"
  - "Database"
---

![](https://assets.bytebytego.com/diagrams/0329-serverlessdb.jpeg)

无服务器数据库会是未来吗？它和传统云数据库有什么不同？

上图中的 Amazon Aurora Serverless，是 Amazon Aurora 的一种按需自动扩缩容配置。

## Aurora Serverless 的关键特性

* Aurora Serverless 可以根据业务需求自动扩容或缩容。例如，一个准备大型促销活动的电商网站，可以在几毫秒内把负载扩展到多个数据库。和普通云数据库需要人工创建和管理实例不同，Aurora Serverless 可以自动启动和关闭。

* 通过把计算层和数据存储层解耦，Aurora Serverless 可以更精确地计费。另外，Aurora Serverless 还可以把 provisioned 实例和 serverless 实例组合在一起，让现有的 provisioned 数据库也能加入 serverless 池。
