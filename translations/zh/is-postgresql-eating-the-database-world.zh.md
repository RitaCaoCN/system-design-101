---
title: "PostgreSQL 正在吞噬数据库世界吗？"
description: "了解 PostgreSQL 的多功能性以及它对数据库格局的影响。"
image: "https://assets.bytebytego.com/diagrams/0237-is-postgresql-eating-the-database-world.png"
createdAt: "2024-02-27"
draft: false
categories:
  - database-and-storage
tags:
  - "PostgreSQL"
  - "Databases"
---

![](https://assets.bytebytego.com/diagrams/0237-is-postgresql-eating-the-database-world.png)

看起来不管是什么场景，PostgreSQL 都能支持。拿不准的时候，你甚至可以直接用 PostgreSQL。

## PostgreSQL 的能力

* **TimeSeries**

  PostgreSQL 可以借助 Timescale 这个强大的时序数据库扩展，高效处理带时间戳的数据。

* **Machine Learning**

  通过 pgVector 和 PostgresML，Postgres 可以支持机器学习能力和向量相似度搜索。

* **OLAP**

  Postgres 可以借助 Hydra、Citus 和 pg_analytics 等工具支持 OLAP。

* **Derived**

  即使是派生出来的数据库，比如 DuckDB、FerretDB、CockroachDB、AlloyDB、YugaByte DB、Supabase 等，也都提供 PostgreSQL。

* **GeoSpatial**

  PostGIS 为 PostgreSQL 增加地理空间能力，让你可以轻松存储、查询和分析地理数据。

* **Search**

  Postgres 的扩展，如 pgroonga、ParadeDB 和 ZomboDB，提供全文搜索、文本索引和数据解析能力。

* **Federated**

  Postgres 可以无缝集成多种数据源，比如 MongoDB、MySQL、Redis、Oracle、ParquetDB、SQLite 等，从而支持联邦查询和数据访问。

* **Graph**

  Apache AGE 和 EdgeDB 是建立在 PostgreSQL 之上的图数据库。另外，pg_graphql 是一个为 Postgres 提供 GraphQL 支持的扩展。
