---
title: "5 个缓存策略"
description: "了解保持缓存与数据库数据同步的 5 种常见缓存策略。"
image: "https://assets.bytebytego.com/diagrams/0374-top-5-caching-strategies.png"
createdAt: "2024-02-22"
draft: false
categories:
  - caching-performance
tags:
  - "Caching"
  - "Data Synchronization"
---

![](https://assets.bytebytego.com/diagrams/0374-top-5-caching-strategies.png)

一旦在架构中引入缓存，缓存与数据库之间的同步就不可避免。

我们来看看保持数据一致的 5 种常见策略。

## 读策略

*   Cache aside（旁路缓存）
*   Read through（读穿透）

## 写策略

*   Write around（绕过写）
*   Write back（回写）
*   Write through（写穿透）

这些缓存策略经常组合使用。例如，Write around 常与 Cache aside 一起用，以确保缓存保持更新。
