---
title: "如何决定使用哪类数据库"
description: "为你的具体需求选择合适数据库的指南。"
image: "https://assets.bytebytego.com/diagrams/0160-database-types.jpg"
createdAt: "2024-02-17"
draft: false
categories:
  - database-and-storage
tags:
  - database selection
  - database types
---

![](https://assets.bytebytego.com/diagrams/0160-database-types.jpg)

如今可选的数据库有成百上千种，比如 Oracle、MySQL、MariaDB、SQLite、PostgreSQL、Redis、ClickHouse、MongoDB、S3、Ceph 等。我们该如何为系统选择合适的架构？我的简短总结如下：

## 数据库类型

* 关系型数据库：几乎什么问题都能靠它们解决。

* 内存存储：速度快、数据量有限，非常适合快速操作。

* 时序数据库：用于存储和管理带时间戳的数据。

* 图数据库：适合处理非结构化对象之间的复杂关系。

* 文档存储：适合存放大体不可变的数据。

* 宽列存储：通常用于大数据、分析、报表等需要反规范化数据的场景。
