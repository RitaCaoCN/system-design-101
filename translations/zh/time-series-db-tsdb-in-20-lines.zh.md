---
title: "20 行解释时序数据库 TSDB"
description: "了解时序数据库（TSDB）及其应用场景。"
image: "https://assets.bytebytego.com/diagrams/0364-time-series-db-tsdb-in-20-lines.jpeg"
createdAt: "2024-02-07"
draft: false
categories:
  - database-and-storage
tags:
  - "Database"
  - "TimeSeries"
---

![](https://assets.bytebytego.com/diagrams/0364-time-series-db-tsdb-in-20-lines.jpeg)

什么是**时序数据库**（Time-Series DB，简称 TSDB）？它和关系型数据库有什么不同？

上图展示了一个典型时序数据库的**内部数据模型**。

TSDB 是针对时间序列数据做了优化的数据库。

* 从用户视角看，数据看起来和关系型数据库的表差不多。但在底层，weather 表会以 \[Measurement, Tag, Field Name] 的格式，存进 4 个 TSM（Time-Structured Merge Trees）中。

* 这样一来，我们就能基于时间和标签快速做聚合与分析。

* 典型用途：

  * 市场中的交易和市场数据更新
  * 服务器指标
  * 应用性能监控
  * 网络数据
  * 传感器数据
  * 事件
  * 点击流
