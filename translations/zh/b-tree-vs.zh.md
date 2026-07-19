---
title: "B-Tree 与 LSM-Tree"
description: "了解 B-Tree 和 LSM-Tree 这两种数据结构的区别。"
image: "https://assets.bytebytego.com/diagrams/0091-btree-lsm.png"
createdAt: "2024-02-16"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Structures"
  - "Databases"
---

![a close up of a chart](https://assets.bytebytego.com/diagrams/0091-btree-lsm.png)

## B-Tree

B-Tree 几乎是所有关系型数据库中最广泛使用的索引数据结构。

B-Tree 中存储信息的基本单元通常叫做一个“page”。查找某个 key 时，会沿着 key 的范围一路向下，直到找到实际值。

## LSM-Tree

LSM-Tree（Log-Structured Merge Tree）被许多 NoSQL 数据库广泛使用，例如 Cassandra、LevelDB 和 RocksDB。

LSM-Tree 会维护 key-value 对，并使用 Sorted Strings Table（SSTable）持久化到磁盘，其中 key 是排序好的。

Level 0 段会定期合并到 Level 1 段。这个过程叫做 **压缩**（compaction）。

最大的区别大概是这样：

* B-Tree 更适合快速读取

* LSM-Tree 更适合快速写入
