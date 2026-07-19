---
title: "6 个数据管理模式"
description: "了解 6 种关键的数据管理模式，提升数据处理效率。"
image: "https://assets.bytebytego.com/diagrams/0379-top-6-data-management-patterns.png"
createdAt: "2024-02-04"
draft: false
categories:
  - database-and-storage
tags:
  - "data management"
  - "data patterns"
---

![](https://assets.bytebytego.com/diagrams/0379-top-6-data-management-patterns.png)

### 以下是 6 种常见的数据管理模式

## Cache Aside

当应用需要访问数据时，会先检查缓存。如果缓存中没有数据（cache miss），就从数据存储中取出数据，写入缓存，然后把数据返回给用户。这个模式特别适合读多写少的场景。

## Materialized View

Materialized View 是一种保存查询结果的数据库对象。它会被物理存储，也就是说数据会真正计算出来并写到磁盘上，而不是每次请求时临时生成。对于复杂计算或聚合查询，这能显著加快查询速度。它尤其适合数据仓库和商业智能场景，在这些场景里查询性能非常关键。

## CQRS

CQRS 是一种把读写数据模型分开的架构模式。也就是说，用于查询数据的结构和用于更新数据的结构是分离的。这样可以分别针对读和写进行优化，从而提升性能、可扩展性和安全性。CQRS 特别适合读写需求差异很大的复杂系统。

## Event Sourcing

Event Sourcing 是一种把应用状态变化按事件序列保存下来的模式。它不只是保存当前状态，而是把领域内发生过的所有变化（事件）都记录下来。这样应用可以重建历史状态，也能提供一条清晰的审计轨迹。它适合复杂业务交易、审计追踪以及需要回放或回滚事件的场景。

## Index Table

Index Table 模式是为数据库创建额外的表，这些表会针对特定查询进行优化。它们充当二级索引，帮助快速检索数据，而不需要扫描完整的主数据存储。这个模式适合大规模数据集，以及那些频繁执行特定查询的场景。

## Sharding

Sharding 是一种数据分区模式，把数据拆成更小、更容易管理的片段，也就是 shard，并把它们放到不同的数据库服务器上。这个模式用于把数据分布到多台机器上，以提升可扩展性和性能。对于高吞吐应用来说，分片尤其有效，因为它可以横向扩展，把负载分散到更多服务器上，支持更多用户和事务。
