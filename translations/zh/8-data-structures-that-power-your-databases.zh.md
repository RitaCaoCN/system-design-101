---
title: "支撑数据库的 8 种数据结构"
description: "了解驱动数据库高效运行的 8 种关键数据结构。"
image: "https://assets.bytebytego.com/diagrams/0181-eight-ds-db.jpg"
createdAt: "2024-03-02"
draft: false
categories:
  - database-and-storage
tags:
  - Data Structures
  - Databases
---

![](https://assets.bytebytego.com/diagrams/0181-eight-ds-db.jpg)

答案会因使用场景而异。数据可以索引在内存中，也可以索引在磁盘上。数据格式同样各不相同，比如数字、字符串、地理坐标等。系统可能是写多读少，也可能是读多写少。所有这些因素都会影响你对数据库索引格式的选择。

下面是一些最常用的数据索引结构：

* **Skiplist（跳表）：**常见的内存索引类型。Redis 中有使用

* **Hash index（哈希索引）：**“Map”（或“Collection”）数据结构的一种非常常见的实现

* **SSTable：**不可变的磁盘版 “Map” 实现

* **LSM tree：**Skiplist + SSTable。具备高写入吞吐

* **B-tree：**基于磁盘的方案。读写性能较为稳定一致

* **Inverted index（倒排索引）：**用于文档索引。Lucene 中有使用

* **Suffix tree（后缀树）：**用于字符串模式搜索

* **R-tree：**多维搜索，例如查找最近邻

这并不是所有数据库索引类型的完整列表。
