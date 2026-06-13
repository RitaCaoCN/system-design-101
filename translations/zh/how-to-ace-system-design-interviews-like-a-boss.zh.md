---
title: "如何搞定系统设计面试"
description: "一个帮助你在系统设计面试中表现出色的 7 步流程。"
image: "https://assets.bytebytego.com/diagrams/0104-how-to-ace-system-design-interviews-like-a-boss.png"
createdAt: '2024-03-14'
draft: false
categories:
  - technical-interviews
tags:
  - "System Design"
  - "Interview Preparation"
---

![系统设计面试](https://assets.bytebytego.com/diagrams/0104-how-to-ace-system-design-interviews-like-a-boss.png)

按照下面这个 7 步流程，可以帮助你在系统设计轮中表现得更好。

## 1. 澄清需求

第一步是澄清功能性需求和非功能性需求。通过提问来理解系统的核心功能，以及数据量、可用性、规模等非功能性方面。

## 2. 容量估算

接下来，估算系统容量。重点关注用户数量、流量、存储和内存需求，以及计算和网络资源需求等指标。

## 3. 创建高层设计

把系统拆分成客户端应用、服务器、负载均衡器、数据库等组件。

可以先画一个简单的方框图，展示这些组件以及它们之间可能的交互关系。重点关注数据流。

## 4. 数据库设计

对数据进行建模，并为系统选择合适的数据库类型。完成之后，再关注数据库 schema 的设计。

## 5. 接口设计

接下来关注系统的接口。这可能包括 API 端点，也可能包括不同组件之间交换的事件模型。同时，还需要选择通信方式，例如 REST、GraphQL、gRPC，或者事件驱动方式。

## 6. 可扩展性和性能

通过提出要使用的技术方案，来处理系统的可扩展性、性能和延迟问题。例如：垂直扩展、水平扩展、缓存、索引、反范式化、分片、复制、CDN 等。

## 7. 可靠性和韧性

最后，处理设计中的可靠性和韧性问题。识别单点故障，并降低它们造成的影响。
