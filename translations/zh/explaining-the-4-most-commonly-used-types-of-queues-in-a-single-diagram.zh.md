---
title: "4 种常用队列解释"
description: "用一张图了解 4 种最常用的队列类型。"
image: "https://assets.bytebytego.com/diagrams/0366-types-of-queues.png"
createdAt: "2024-02-06"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Structures"
  - "Queues"
---

![](https://assets.bytebytego.com/diagrams/0366-types-of-queues.png)

队列是系统中非常常用的数据结构。上图展示了我们经常用到的 4 种队列。

## 简单 FIFO 队列

简单队列遵循 FIFO（First In First Out，先进先出）。新元素插入到队尾，取出元素时从队头移除。

比如，每当收到一笔支付响应时，我们想给用户发送邮件通知，就可以用 FIFO 队列。邮件会按支付响应到达的相同顺序发出。

## 环形队列

环形队列也叫 circular buffer（环形缓冲区）或 ring buffer。它的最后一个元素会连回第一个元素。插入发生在队列前端，删除发生在队列末端。

一个著名的实现是 LMAX 的低延迟 ring buffer。交易组件之间通过 ring buffer 通信。它实现在内存中，速度极快。

## 优先队列

优先队列中的元素有预定义的优先级。我们会从队列中取出优先级最高（或最低）的元素。底层通常用最大堆或最小堆实现，堆顶就是优先级最高或最低的元素。

典型用法是：把病情最严重的患者送到急诊室，其他患者则去普通诊室。

## 双端队列（Deque）

Deque 也叫 double-ended queue（双端队列）。插入和删除都可以在队头和队尾进行。Deque 同时支持 FIFO 和 LIFO（Last In First Out，后进先出），因此也能用来实现栈。
