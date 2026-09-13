---
title: "每个开发者都该了解的缓存系统"
description: "了解开发者优化性能时常用的关键缓存层。"
image: "https://assets.bytebytego.com/diagrams/0418-cache-systems-every-developer-should-know.jpeg"
createdAt: "2024-02-20"
draft: false
categories:
  - caching-performance
tags:
  - Caching
  - Performance
---

![](https://assets.bytebytego.com/diagrams/0418-cache-systems-every-developer-should-know.jpeg)

从面向客户端的一侧到后端系统，数据几乎无处不在地被缓存。我们来看看这些缓存层：

## 缓存层

1.  客户端应用：浏览器会缓存 HTTP 响应。服务器响应里通过 Header 给出缓存指令。后续请求时，如果缓存仍然新鲜，浏览器可以直接返回缓存数据。

2.  内容分发网络（CDN）：CDN 会缓存图片、样式表、JavaScript 等静态内容。它们从更靠近用户的节点提供缓存内容，从而降低延迟和加载时间。

3.  负载均衡器：有些负载均衡器会缓存高频请求的数据。这样可以在不访问后端服务器的情况下返回响应，降低负载并缩短响应时间。

4.  消息代理：像 Kafka 这类系统，可以按保留策略把消息缓存在磁盘上。消费者再按自己的节奏拉取消息。

5.  服务：单个服务常会使用缓存来加快数据读取，先查内存缓存，再查数据库。对于更大的数据集，服务也可能使用磁盘缓存。

6.  分布式缓存：像 Redis 这类系统会在服务之间缓存键值对，读写通常比传统数据库更快。

7.  全文搜索引擎：像 Elasticsearch 这类平台会为数据建立索引，以便高效文本检索。这种索引本质上也是一种为快速文本检索优化过的缓存形态。

8.  数据库：数据库里也有一些专门提升性能的机制，其中部分就包含缓存思想：

### 数据库中的缓存机制

*   **缓冲池（Bufferpool）：** 数据库内部的缓存，保存数据页副本。它支持在内存临时存储中快速读写，减少访问磁盘的需要。

*   **物化视图（Materialized Views）：** 类似缓存，会保存计算开销很大的查询结果。数据库可以直接快速返回这些预计算结果，而不必每次重新计算。
