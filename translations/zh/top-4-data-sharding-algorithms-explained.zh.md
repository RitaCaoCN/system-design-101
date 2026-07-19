---
title: "4 种数据分片算法"
description: "了解适用于高效数据管理的 4 种主流数据分片算法。"
image: "https://assets.bytebytego.com/diagrams/0373-top-4-data-sharding-algorithms-explained.png"
createdAt: "2024-02-21"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Sharding"
  - "Algorithms"
---

![](https://assets.bytebytego.com/diagrams/0373-top-4-data-sharding-algorithms-explained.png)

我们处理的是海量数据。很多时候，我们需要把数据拆成更小、更容易管理的片段，也就是“shard”。下面是一些常见的数据分片算法：

## 基于范围的分片

这种方法根据值的范围来划分数据。例如，客户数据可以按姓氏字母顺序分片，交易数据可以按日期范围分片。

## 基于哈希的分片

这种方法会对从数据中选出的 shard key 进行哈希运算，比如 customer ID 或 transaction ID。

和基于范围的分片相比，这种方式通常可以更均匀地把数据分布到各个 shard 上。不过，我们需要选择合适的哈希函数，以避免哈希冲突。

## 一致性哈希

这是基于哈希分片的扩展形式，可以减少新增或删除 shard 时带来的影响。它能更均匀地分布数据，并在 shard 增减时最小化需要迁移的数据量。

## 虚拟桶分片

数据先映射到虚拟桶，再由虚拟桶映射到物理 shard。这种两级映射让 shard 管理和重平衡更灵活，而且不会造成太多数据移动。
