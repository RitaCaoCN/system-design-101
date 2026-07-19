---
title: "为什么 PostgreSQL 最受喜爱"
description: "了解 PostgreSQL 在 2022 年调查中被评为最受喜爱的数据库的原因。"
image: "https://assets.bytebytego.com/diagrams/0303-postgres.png"
createdAt: "2024-02-25"
draft: false
categories:
  - database-and-storage
tags:
  - "PostgreSQL"
  - "Database"
---

![](https://assets.bytebytego.com/diagrams/0303-postgres.png)

图中展示了 PostgreSQL 的许多使用场景，这是一款几乎覆盖开发者所需 **全部场景** 的数据库。

## PostgreSQL 的使用场景

* **OLTP（Online Transaction Processing）**

  我们可以用 PostgreSQL 处理 CRUD（Create-Read-Update-Delete）操作。

* **OLAP（Online Analytical Processing）**

  我们可以用 PostgreSQL 做分析处理。PostgreSQL 基于 **HTAP**（Hybrid transactional/analytical processing）架构，因此能很好地同时处理 OLTP 和 OLAP。

* **FDW（Foreign Data Wrapper）**

  FDW 是 PostgreSQL 的一个扩展，允许我们从另一个数据库访问某个表或 schema。

* **Streaming**

  PipelineDB 是 PostgreSQL 的一个扩展，专门用于高性能时序聚合，适合驱动实时报表和分析应用。

* **Geospatial**

  PostGIS 是 PostgreSQL 的空间数据库扩展，为 PostgreSQL 对象关系数据库增加地理对象支持，使我们可以在 SQL 中运行位置查询。

* **Time Series**

  Timescale 对 PostgreSQL 做了时序和分析扩展。例如，开发者可以把持续不断的金融和 tick 数据流与其他业务数据结合起来，构建新应用并发现独特洞察。

* **Distributed Tables**

  CitusData 通过分布式数据和查询来扩展 Postgres。
