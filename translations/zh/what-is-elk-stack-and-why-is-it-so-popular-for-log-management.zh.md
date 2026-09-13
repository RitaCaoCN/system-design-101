---
title: "什么是 ELK Stack，为什么它很流行？"
description: "了解 ELK Stack：Elasticsearch、Logstash 与 Kibana。"
image: "https://assets.bytebytego.com/diagrams/0183-elk.jpg"
createdAt: "2024-02-15"
draft: false
categories:
  - caching-performance
tags:
  - "ELK Stack"
  - "Log Management"
---

![](https://assets.bytebytego.com/diagrams/0183-elk.jpg)

ELK Stack 由三个开源产品组成。ELK 分别代表 Elasticsearch、Logstash 和 Kibana。

*   Elasticsearch 是一个全文搜索与分析引擎，核心基于 Apache Lucene 搜索引擎。

*   Logstash 从各类边缘采集器收集数据，完成转换后再发送到不同目的地，供后续处理或可视化使用。

为了扩展边缘数据接入能力，后来又推出了 Beats：安装在边缘主机上的轻量级代理，负责采集日志并发送到 Logstash。

*   Kibana 是可视化层，用户可以用它来分析与展示数据。

上图展示了 ELK Stack 的工作方式：

## ELK Stack 工作流

步骤 1 - Beats 从各种数据源采集数据。例如，Filebeat 和 Winlogbeat 处理日志，Packetbeat 处理网络流量。

步骤 2 - Beats 把数据发送到 Logstash，进行聚合与转换。如果数据量很大，可以加入消息队列（如 Kafka）来解耦生产者与消费者。

步骤 3 - Logstash 把数据写入 Elasticsearch，完成索引与存储。

步骤 4 - Kibana 构建在 Elasticsearch 之上，为用户提供各类搜索工具和仪表盘，用于可视化数据。

ELK Stack 很适合做故障排查与监控。它以相对合理的价格，在日志分析领域提供了一套简单且稳健的方案，因此变得非常流行。
