---
title: "CAP 定理：最容易被误解的术语之一"
description: "了解 CAP 定理、它的含义，以及常见误解。"
image: "https://assets.bytebytego.com/diagrams/0131-cap-theorem.jpeg"
createdAt: "2024-03-06"
draft: false
categories:
  - database-and-storage
tags:
  - "distributed systems"
  - "cap theorem"
---

![a close up of text and logo over a white background](https://assets.bytebytego.com/diagrams/0131-cap-theorem.jpeg)

CAP 定理是计算机科学中最著名的术语之一，但我敢打赌，不同开发者对它的理解并不一样。我们来看看它到底是什么，以及为什么容易让人困惑。

CAP 定理指出：一个分布式系统不能同时提供以下三项保证中的两项以上。

## 一致性（Consistency）

一致性意味着：无论客户端连到哪个节点，所有客户端在同一时刻看到的数据都一样。

## 可用性（Availability）

可用性意味着：即使部分节点宕机，任何请求数据的客户端都能得到响应。

## 分区容错（Partition Tolerance）

分区容错意味着：即使出现网络分区，系统仍能继续运行。

“三选二”的表述很有用，但这种简化也可能产生误导。

* 挑选数据库并不容易。仅凭 CAP 定理来合理化我们的选择是不够的。例如，公司不会只因为 Cassandra 是 AP 系统，就用它来做聊天应用。是一长串优质特性，让 Cassandra 成为存储聊天消息的理想选项之一。我们需要挖得更深。

* “CAP 只禁止了设计空间中很小的一部分：在分区出现时同时做到完美的可用性和一致性，而这种分区其实很少见。”引自论文：*CAP Twelve Years Later: How the “Rules” Have Changed*。

* 这个定理讨论的是 100% 的可用性和一致性。更现实的讨论，其实是在没有网络分区时，延迟和一致性之间的取舍。更多细节见 PACELC 定理。

## CAP 定理真的有用吗？

我认为它仍然有用，因为它打开了我们的思路，引出一组取舍讨论；但它只是故事的一部分。在选择正确的数据库时，我们还需要挖得更深。
