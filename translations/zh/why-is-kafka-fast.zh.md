---
title: "Kafka 为什么快？"
description: "了解 Kafka 高性能背后的关键设计选择。"
image: "https://assets.bytebytego.com/diagrams/0424-why-is-kafka-fast.jpg"
createdAt: "2024-02-05"
draft: false
categories:
  - database-and-storage
tags:
  - "Kafka"
  - "Performance"
---

![No alternative text description for this image](https://assets.bytebytego.com/diagrams/0424-why-is-kafka-fast.jpg)

Kafka 的高性能来自很多设计决定。这里我们重点看两个，我们认为这两个最关键。

## 顺序 I/O

第一个是 Kafka 对 **顺序 I/O** 的依赖。

## 零拷贝

第二个为 Kafka 带来性能优势的设计，是它对效率的极致追求，也就是 **零拷贝** 原则。

上图展示了数据在 producer 和 consumer 之间是如何传输的，以及零拷贝具体是什么意思。

* 第 1.1 - 1.3 步：Producer 把数据写入磁盘
* 第 2 步：Consumer 在没有零拷贝时读取数据
  * 2.1：数据从磁盘加载到 OS 缓存
  * 2.2：数据从 OS 缓存复制到 Kafka 应用程序
  * 2.3：Kafka 应用程序把数据复制到 socket buffer
  * 2.4：数据从 socket buffer 复制到网卡
  * 2.5：网卡把数据发送给 consumer
* 第 3 步：Consumer 在使用零拷贝时读取数据
  * 3.1：数据从磁盘加载到 OS 缓存
  * 3.2：OS 缓存通过 `sendfile()` 直接把数据复制到网卡
  * 3.3：网卡把数据发送给 consumer

零拷贝是一种减少数据在应用上下文和内核上下文之间多次复制的捷径。
