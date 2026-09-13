---
title: "Redis 大 Key 如何影响持久化"
description: "了解大 Key 如何影响 Redis 的 AOF 持久化模式。"
image: "https://assets.bytebytego.com/diagrams/0085-big-keys.png"
createdAt: "2024-02-17"
draft: false
categories:
  - caching-performance
tags:
  - "Redis"
  - "Persistence"
---

![](https://assets.bytebytego.com/diagrams/0085-big-keys.png)

我们把包含大量数据的 key 称为大 Key。例如，某个 key 的大小达到 5 MB。

上图展示了大 Key 如何影响 Redis 的 AOF（Append-Only-File）持久化。

开启 AOF 持久化时，有三种模式：

*   Always - 内存中每次有数据更新，都同步写入磁盘。

*   EverySec - 每秒写入一次磁盘。

*   No - Redis 不控制何时落盘，而是由操作系统决定何时把数据写入磁盘。

## 如何分析大 Key 的影响？

Redis 会先把 key 写入内存，再调用 `write()` 把数据写到内核缓冲区缓存；随后 `fsync()` 会把该文件中已修改的内存数据刷到磁盘设备。三种模式的差异如下。

在 “Always” 模式下，会同步调用 `fsync()`。如果要更新一个大 Key，主线程会被阻塞，因为它必须等待写操作完成。

“EverySec” 会启动一个后台定时任务，每秒调用一次 `fsync()`，因此大 Key 不会影响 Redis 主线程。

“No” 模式从不调用 `fsync()`，完全交给操作系统。大 Key 也不会影响主线程。
