---
title: "用 Avro 实现平滑数据迁移"
description: "了解 Apache Avro 如何通过 schema 演进帮助完成平滑的数据迁移。"
image: "https://assets.bytebytego.com/diagrams/0080-avro.png"
createdAt: "2024-02-01"
draft: false
categories:
  - database-and-storage
tags:
  - "Data Migration"
  - "Apache Avro"
---

![](https://assets.bytebytego.com/diagrams/0080-avro.png)

我们在做数据迁移时，怎么保证迁移过程顺利？上图展示了 Apache Avro 是如何在数据迁移中处理 schema 演进的。

Avro 起源于 2009 年，最初是 Apache Hadoop 的一个子项目，用来解决 Thrift 在 Hadoop 场景中的局限。Avro 主要用于两件事：数据序列化和 RPC。

图中的关键点：

* 我们可以把数据导出为 **对象容器文件**，让 schema 和数据块放在一起。Avro 会根据列结构 **动态** 生成 schema，所以如果 schema 发生变化，就会生成新的 schema，并和新数据一起保存。

* 当导出的文件被加载到另一个数据存储中时，例如 Teradata，任何人都可以读取 schema，从而知道应该如何读取数据。旧数据和新数据都能顺利迁移到新的数据库中。

  和 gRPC 或 Thrift 这类静态生成 schema 的方案不同，Avro 让数据迁移过程更容易。
