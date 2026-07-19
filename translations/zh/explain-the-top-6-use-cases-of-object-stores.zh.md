---
title: "对象存储的 6 个使用场景"
description: "了解对象存储在现代数据管理中的 6 个主要使用场景。"
image: "https://assets.bytebytego.com/diagrams/0117-explain-the-top-6-use-cases-of-object-stores.png"
createdAt: "2024-02-14"
draft: false
categories:
  - database-and-storage
tags:
  - "Object Storage"
  - "Data Management"
---

![](https://assets.bytebytego.com/diagrams/0117-explain-the-top-6-use-cases-of-object-stores.png)

什么是对象存储？

对象存储用 object 来存数据。它和文件存储不同，文件存储用层级结构来保存文件；也和块存储不同，块存储把文件切成等大小的 block。对象存储会把 metadata 和对象本身一起保存。典型产品包括 AWS S3、Google Cloud Storage 和 Azure Blob Storage。

对象存储在格式上更灵活，也更容易扩展。

## 场景 1：数据归档

随着业务数据不断增长，我们不可能把所有数据都放在核心存储系统里。我们需要分层的存储方案。对象存储可以用来归档老数据，比如审计记录或客户对账单。这是一种成本很高效的做法。

## 场景 2：非结构化数据存储

我们经常需要处理非结构化数据或半结构化数据。过去，它们通常会以 blob 的形式存进关系型数据库，效率很低。对象存储非常适合音乐、视频和文本文件。像 Spotify 或 Netflix 这样的公司会用对象存储来持久化媒体文件。

## 场景 3：云原生存储

对于云原生应用，我们需要存储系统具备灵活性和可扩展性。主流公有云厂商都提供很容易接入的对象存储产品，它们是很经济的存储选择。

## 场景 4：数据湖

分布式系统里会有很多类型的数据。基于对象存储的数据湖，可以给不同业务线提供一个地方，把数据先汇聚起来，供后续分析或机器学习使用。对象存储高效的读写能力，还能支撑更多下游数据处理步骤，比如 ETL（Extract-Transform-Load）或者构建数据仓库。

## 场景 5：物联网（IoT）

IoT 传感器会产生各种各样的数据。对象存储可以保存这类时序数据，之后再拿去做分析或 AI 算法。主流公有云厂商也提供把原始 IoT 数据接入对象存储的管道。

## 场景 6：备份与恢复

对象存储可以用来保存数据库或文件系统备份。之后，这些备份可以被加载出来，用于快速恢复。这提升了系统的可用性。
