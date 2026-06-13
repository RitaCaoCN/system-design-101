---
title: "必须掌握的系统设计构建块"
description: "构建可扩展应用所需的核心系统设计组件。"
image: "https://assets.bytebytego.com/diagrams/0285-must-know-system-design-building-blocks.png"
createdAt: "2024-02-11"
draft: false
categories:
  - cloud-distributed-systems
tags:
  - "system design"
  - "scalability"
---

![](https://assets.bytebytego.com/diagrams/0285-must-know-system-design-building-blocks.png)

这些构建块可以分为 6 个大类。

## 分布式计算

* 分布式消息队列支持异步通信，并帮助服务之间解耦。

* 分布式缓存把频繁访问的数据存储在内存中，从而提升性能。

* 分布式任务调度器负责管理和协调任务的执行。

## 可扩展性和性能

* 服务扩缩容可以帮助服务根据需求变化调整容量。

* CDN 从地理位置更近的节点提供内容，从而提升性能并降低延迟。

* 一致性哈希可以在节点增加或删除时，尽量减少 key 的重新映射。

## 服务管理

* 服务发现让服务能够找到彼此并进行通信，而不需要在代码中硬编码网络位置。

## 网络和通信

* DNS 把人类可读的域名转换成 IP 地址。

* 负载均衡器把进入系统的网络流量分发到多台服务器。

* API 网关作为一组微服务的统一入口。

## 数据存储和管理

* 数据库负责存储和管理结构化数据。

* 对象存储用于存储图片、视频、文档等复杂对象。

* 分片可以把数据水平拆分到多个节点上。

* 复制通过把数据拷贝到多个节点，帮助数据库进行水平扩展。

## 可观测性和韧性

通过指标、日志和追踪，获得对系统内部状态的洞察。
