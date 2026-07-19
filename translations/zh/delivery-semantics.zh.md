---
title: "交付语义"
description: "理解最多一次、至少一次和恰好一次交付语义。"
image: "https://assets.bytebytego.com/diagrams/0165-delivery-semantics.png"
createdAt: "2024-02-10"
draft: false
categories:
  - database-and-storage
tags:
  - "Message Queues"
  - "Delivery Semantics"
---

![](https://assets.bytebytego.com/diagrams/0165-delivery-semantics.png)

在现代架构中，系统会被拆成一个个小而独立的构建块，它们之间通过定义清晰的接口协作。消息队列为这些构建块提供通信与协调能力。今天，我们来讨论不同的交付语义：最多一次（at-most once）、至少一次（at-least once）和恰好一次（exactly once）。

## 最多一次（At-most once）

顾名思义，最多一次意味着一条消息不会被投递超过一次。消息可能丢失，但不会被重复投递。从高层上看，最多一次交付大致是这样工作的。

### 适用场景：

* 适合监控指标这类场景，少量数据丢失可以接受。

## 至少一次（At-least once）

在这种数据交付语义下，同一条消息可以被投递不止一次，但不能丢失消息。

### 适用场景：

* 至少一次语义下，消息不会丢，但同一条消息可能被投递多次。对用户体验来说并不理想，但通常已经够用——只要重复数据不是大问题，或者消费者端可以去重。
* 例如，如果每条消息都有唯一键，那么在把重复数据写入数据库时就可以直接拒绝。

## 恰好一次（Exactly once）

恰好一次是最难实现的交付语义。它对流畅的用户体验很友好，但对系统性能和复杂度的代价很高。

### 适用场景：

* 金融相关场景（支付、交易、记账等）。当重复不可接受，且下游服务或第三方又不支持幂等时，恰好一次尤为重要。
