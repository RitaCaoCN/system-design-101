---
title: "使用缓存时要考虑的事情"
description: "构建快速在线系统时，使用缓存最该关注的 5 件事。"
image: "https://assets.bytebytego.com/diagrams/0362-things-to-consider-when-using-cache.png"
createdAt: "2024-02-23"
draft: false
categories:
  - caching-performance
tags:
  - "Caching"
  - "Performance"
---

![](https://assets.bytebytego.com/diagrams/0362-things-to-consider-when-using-cache.png)

缓存是构建快速在线系统时**最常用**的技术之一。使用缓存时，下面这 5 点最值得关注：

这份速查表的第一版由嘉宾作者 [Love Sharma](https://twitter.com/Zonito87) 撰写。

## 适用场景

*   内存方案

*   读多写少的系统

*   数据更新不频繁

## 缓存技术

*   Cache aside

*   Write-through

*   Read-through

*   Write-around

*   Write-back

## 缓存淘汰算法

*   最近最少使用（LRU）

*   最不经常使用（LFU）

*   先进先出（FIFO）

*   随机替换（RR）

## 关键指标

*   缓存命中率（Cache Hit Ratio）

*   延迟（Latency）

*   吞吐量（Throughput）

*   失效速率（Invalidation Rate）

*   内存使用量（Memory Usage）

*   CPU 使用率

*   网络使用量

## 其他问题

*   冷启动时的惊群问题（Thunder herd）

*   生存时间（TTL）
