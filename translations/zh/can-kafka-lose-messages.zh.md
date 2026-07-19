---
title: "Kafka 会丢消息吗？"
description: "探讨 Kafka 可能丢消息的场景，以及如何防止消息丢失。"
image: "https://assets.bytebytego.com/diagrams/0130-can-kafka-lose-messages.png"
createdAt: "2024-02-12"
draft: false
categories:
  - "database-and-storage"
tags:
  - "Kafka"
  - "Message Loss"
---

错误处理是构建可靠系统时最重要的部分之一。

今天我们来讨论一个重要话题：Kafka 会丢消息吗？

![](https://assets.bytebytego.com/diagrams/0130-can-kafka-lose-messages.png)

很多开发者有一个常见印象：Kafka 天生不会丢消息。但要真正理解它的架构和配置，才能知道它在什么情况下可能丢消息，以及更重要的，如何避免这些情况。

上图展示了消息在 Kafka 生命周期中可能丢失的方式。

## Producer

当我们调用 `producer.send()` 发送消息时，它不会直接发到 broker。整个消息发送过程里涉及两个线程和一个队列：

* Application thread
* Record accumulator
* Sender thread（I/O 线程）

我们需要给 producer 配置合适的 `acks` 和 `retries`，确保消息能送到 broker。

## Broker

在正常运行时，broker 集群不应该丢消息。不过，我们需要理解一些极端情况，它们可能导致消息丢失：

* 为了更高的 I/O 吞吐，消息通常会异步刷新到磁盘。如果实例在刷新前就宕机，消息就会丢失。

* Kafka 集群里的副本必须正确配置，才能保留一份有效数据副本。数据同步的确定性非常重要。

## Consumer

Kafka 提供了不同的消息提交方式。自动提交可能会在消息还没真正处理完之前，就先把记录确认掉。这样当 consumer 在处理中间崩溃时，有些记录可能永远不会被处理。

一个更好的做法，是把同步提交和异步提交结合起来：在处理循环里使用异步提交来获得更高吞吐；在异常处理里使用同步提交，确保最后一个 offset 一定被提交。
