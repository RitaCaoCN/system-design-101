---
title: "纠删码"
description: "了解纠删码：如何提升对象存储中的数据持久性。"
image: "https://assets.bytebytego.com/diagrams/0187-erasure-coding.png"
createdAt: "2024-02-09"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Storage"
  - "Data Redundancy"
---

![](https://assets.bytebytego.com/diagrams/0187-erasure-coding.png)

在 S3 这类对象存储中，有一种很酷、也很常用的提升持久性的技术，叫做**纠删码**（Erasure Coding）。我们来看看它是怎么工作的。

纠删码处理数据持久性的方式，和复制（replication）不同。它会把数据切成更小的块（放在不同服务器上），并生成校验块（parity）来提供冗余。发生故障时，我们可以用数据块和校验块把数据重建回来。下面看图 1 中的具体例子（4 + 2 纠删码）。

* 数据被切成四个大小相等的数据块：d1、d2、d3、d4。

* 用数学公式计算出校验块 p1 和 p2。举一个非常简化的例子：p1 = d1 + 2\*d2 - d3 + 4\*d4，p2 = -d1 + 5\*d2 + d3 - 3\*d4。

* 由于节点宕机，数据 d3 和 d4 丢失了。

* 再用数学公式，结合已知的 d1、d2、p1、p2，把丢失的 d3 和 d4 重建出来。

纠删码需要多少额外空间？每两个数据块需要一个校验块，所以存储开销是 50%（见图 2）。而三副本复制的存储开销是 200%（见图 2）。

纠删码能提高数据持久性吗？假设一个节点的年故障率是 0.81%。根据 Backblaze 的计算，纠删码可以达到 11 个 9 的持久性，而三副本复制只能达到 6 个 9 的持久性。
