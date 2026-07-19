---
title: "一致性哈希解释"
description: "了解一致性哈希的原理、优势以及真实世界中的应用。"
image: "https://assets.bytebytego.com/diagrams/0151-consistent-hashing.png"
createdAt: "2024-03-07"
draft: false
categories:
  - database-and-storage
tags:
  - "Consistent Hashing"
  - "Distributed Systems"
---

![](https://assets.bytebytego.com/diagrams/0151-consistent-hashing.png)

## 算法 1：一致性哈希

Amazon DynamoDB、Apache Cassandra、Discord 和 Akamai CDN 有什么共同点？

它们都使用了一致性哈希。下面直接进入正题。

## 简单哈希有什么问题？

在大规模分布式系统中，数据通常无法放进单台服务器里，而是要“分布”在多台机器上。这就是所谓的水平扩展。

为了构建一个性能可预测的系统，必须尽量把数据均匀地分布到这些服务器上。

简单哈希的方式是：`serverIndex = hash(key) % N`，其中 `N` 是服务器池的大小。

当集群规模固定、数据分布也比较均匀时，这种方式工作得很好。但当为了应对增长需求而增加服务器，或者当某些服务器被移除时，就会引发大量缓存未命中，并导致很多对象被迁移。

## 一致性哈希

一致性哈希就是用来缓解这个问题的一种有效技术。

它的目标很简单：即使服务器数量发生变化，也希望绝大多数对象仍然被分配到原来的那台服务器上。

如图所示，我们用哈希函数对每台服务器的名字或 IP 地址进行哈希，把服务器放到一个哈希环上。接着，再用同一个哈希函数对每个对象的 key 进行哈希。

要找到某个对象应该落在哪台服务器上，就从该对象 key 在环上的位置开始，沿顺时针方向查找，直到找到第一台服务器。继续这个例子，key 0 落在 server 0 上，key 1 落在 server 1 上。

现在来看一下新增服务器时会发生什么。

这里我们把一台新服务器 `s4` 插入到哈希环上 `s0` 的左侧。注意，此时只有 `k0` 需要从 `s0` 迁移到 `s4`。这是因为从 `k0` 在环上的位置顺时针走，最先遇到的服务器现在变成了 `s4`。而 `k1`、`k2`、`k3` 都不会受到影响。

## 一致性哈希在真实世界中的应用

* **Amazon DynamoDB 和 Apache Cassandra：** 在重新平衡数据时尽量减少数据迁移。

* **像 Akamai 这样的 CDN：** 将 Web 内容更均匀地分布到各个边缘节点。

* **像 Google Network Load Balancer 这样的负载均衡器：** 将持久连接更均匀地分配到后端服务器。
