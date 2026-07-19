---
title: "IBM MQ -> RabbitMQ -> Kafka -> Pulsar：消息队列演进"
description: "了解消息队列架构的演进：从 IBM MQ 到 Pulsar。"
image: "https://assets.bytebytego.com/diagrams/0271-message-queue-evolve.png"
createdAt: "2024-03-05"
draft: false
categories:
  - "database-and-storage"
tags:
  - "Message Queues"
  - "System Design"
---

![Message Queue Evolution](https://assets.bytebytego.com/diagrams/0271-message-queue-evolve.png)

* IBM MQ

IBM MQ 于 1993 年推出。它最初叫 MQSeries，2002 年改名为 WebSphere MQ，2014 年再改名为 IBM MQ。IBM MQ 是一款非常成功的产品，在金融行业被广泛使用。到 2020 年，它的收入仍然达到 10 亿美元。

* RabbitMQ

RabbitMQ 的架构与 IBM MQ 不同，更接近 Kafka 的一些概念。生产者带着指定的 exchange type 把消息发布到 exchange。exchange type 可以是 direct、topic 或 fanout。然后，exchange 再根据不同的消息属性和 exchange type，把消息路由到各个队列。消费者再相应地取出消息。

* Kafka

2011 年初，LinkedIn 开源了 Kafka，它是一个分布式事件流平台。其名字来自 Franz Kafka。正如名字所暗示的，Kafka 针对写入做了优化。它为处理实时数据流提供了一个高吞吐、低延迟的平台。它通过统一的事件日志实现事件流式处理，在互联网公司中被广泛使用。

Kafka 定义了 producer、broker、topic、partition 和 consumer。它的简洁性和容错能力，使它能够取代以前那些基于 AMQP 的消息队列产品。

* Pulsar

Pulsar 最初由 Yahoo 开发，是一个一体化的消息与流处理平台。和 Kafka 相比，Pulsar 吸收了许多其他产品中实用的特性，并支持更广的能力范围。此外，Pulsar 的架构更偏云原生，对集群扩缩容、分区迁移等支持更好。

Pulsar 架构有两层：服务层（serving layer）和持久化层（persistent layer）。Pulsar 原生支持分层存储，我们可以利用 AWS S3 这类更便宜的对象存储，把消息持久化保存更长时间。
