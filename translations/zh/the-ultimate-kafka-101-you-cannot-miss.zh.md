---
title: "终极 Kafka 101"
description: "用 8 个简单步骤了解 Kafka 的基础知识。"
image: "https://assets.bytebytego.com/diagrams/0246-kafka-101-8-steps-to-learn-the-fundamentals-of-kafka.png"
createdAt: "2024-02-02"
draft: false
categories:
  - database-and-storage
tags:
  - "Kafka"
  - "Distributed Systems"
---

![](https://assets.bytebytego.com/diagrams/0246-kafka-101-8-steps-to-learn-the-fundamentals-of-kafka.png)

Kafka 很流行，但一开始也很容易让人觉得信息量很大。

下面这 8 个简单步骤，可以帮助你理解 Kafka 的基础知识。

## Kafka 是什么？

Kafka 是一个分布式事件存储和流处理平台。它最初是 LinkedIn 内部项目，如今已经支撑起 Netflix、Uber 等公司里一些最大的 数据 管道。

## Kafka 消息

消息是 Kafka 中最基本的数据单元。它就像表中的一条记录，由 header、key 和 value 组成。

## Kafka 主题和分区

每条消息都会进入某个 Topic。可以把 topic 想成电脑里的一个文件夹。Topic 下面还会有多个 partition。

## Kafka 的优势

Kafka 可以同时处理多个生产者和消费者，同时提供基于磁盘的数据保留能力和很强的扩展性。

## Kafka Producer

Kafka 中的 producer 负责创建新消息，把消息批量打包后发送到 Kafka topic。它们还负责在不同 partition 之间均衡消息。

## Kafka Consumer

Kafka consumer 会以 consumer group 的形式协同工作，从 broker 中读取消息。

## Kafka 集群

Kafka 集群由多个 broker 组成，每个 partition 都会复制到多个 broker 上，以确保高可用和冗余。

## Kafka 的使用场景

Kafka 可以用于日志分析、数据流处理、变更数据捕获以及系统监控。
