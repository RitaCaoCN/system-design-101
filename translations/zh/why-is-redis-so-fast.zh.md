---
title: "Redis 为什么这么快？"
description: "了解 Redis 速度惊人的几个关键原因。"
image: "https://assets.bytebytego.com/diagrams/0422-why-is-redis-so-fast.png"
createdAt: '2024-03-07'
draft: false
categories:
  - caching-performance
tags:
  - "Redis"
  - "Performance"
---

![](https://assets.bytebytego.com/diagrams/0422-why-is-redis-so-fast.png)

主要有 3 个原因，如图所示。

* Redis 是一个基于 RAM 的数据库。RAM 的访问速度至少比随机磁盘访问快 1000 倍。

* Redis 使用 I/O 多路复用和单线程事件循环来提高执行效率。

* Redis 还利用了多种高效的底层数据结构。
