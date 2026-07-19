---
title: "终极 Redis 101"
description: "通过这些简单步骤学习 Redis 的基础知识。"
image: "https://assets.bytebytego.com/diagrams/0009-steps-to-learn-the-fundamentals-of-redis-101.png"
createdAt: "2024-02-19"
draft: false
categories:
  - caching-performance
tags:
  - "Redis"
  - "Database"
---

![](https://assets.bytebytego.com/diagrams/0009-steps-to-learn-the-fundamentals-of-redis-101.png)

Redis 是世界上最流行的数据存储之一，而且功能非常丰富。

下面这 8 个简单步骤，可以帮助你理解 Redis 的基础知识。

## 什么是 Redis？

Redis（Remote Dictionary Server）是一个多模型数据库，能够提供亚毫秒级延迟。Redis 的核心思想之一是：缓存不仅可以当缓存，也可以作为一个完整的数据库来使用。

## Redis 的采用情况

Airbnb、Uber、Slack 等高流量互联网网站，都已经在自己的技术栈中采用了 Redis。

## Redis 如何改变数据库格局？

Redis 支持基于主内存的读写，同时也支持完整的持久化存储。读写请求直接在主内存中处理，但数据也会被持久化到磁盘上。这通常通过快照（RDB）和 AOF 来完成。

## Redis 数据结构

Redis 以键值对格式存储数据。它支持多种数据结构，例如字符串、位图、列表、集合、有序集合、哈希、JSON 等。

## Redis 基础命令

常用的 Redis 命令包括 `SET`、`GET`、`DELETE`、`INCR`、`HSET` 等，当然还远不止这些。

## Redis 模块

Redis 模块是对 Redis 核心能力的扩展插件。一些常见模块包括 RediSearch、RedisJSON、RedisGraph、RedisBloom、RedisAI、RedisTimeSeries、RedisGears、RedisML 等。

## Redis Pub/Sub

Redis 还支持基于发布-订阅通信模型的事件驱动架构。

## Redis 的使用场景

Redis 最常见的使用场景包括分布式缓存、会话存储、消息队列、限流、高速数据库等。
