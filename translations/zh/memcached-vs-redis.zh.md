---
title: "Memcached 与 Redis"
description: "了解 Memcached 与 Redis 在缓存场景下的关键差异。"
image: "https://assets.bytebytego.com/diagrams/0267-memcached-redis.jpg"
createdAt: "2024-02-25"
draft: false
categories:
  - caching-performance
tags:
  - "memcached"
  - "redis"
---

![](https://assets.bytebytego.com/diagrams/0267-memcached-redis.jpg)

常见面试题：Redis 和 Memcached 有什么区别？

上图展示了关键差异。丰富的数据结构让 Redis 很适合这些场景：

*   记录每篇文章的点击数与评论数（hash）

*   对评论用户列表排序，并做用户去重（zset）

*   缓存用户行为历史，并过滤恶意行为（zset、hash）

*   用很小的空间存储超大规模数据的布尔信息。例如登录状态、会员状态（bitmap）
