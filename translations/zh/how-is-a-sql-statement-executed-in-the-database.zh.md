---
title: "SQL 语句在数据库中如何执行"
description: "了解 SQL 语句在数据库系统中的执行步骤。"
image: "https://assets.bytebytego.com/diagrams/0340-sql-execution-order-in-db.jpeg"
createdAt: "2024-02-23"
draft: false
categories:
  - database-and-storage
tags:
  - SQL
  - Database Internals
---

![](https://assets.bytebytego.com/diagrams/0340-sql-execution-order-in-db.jpeg)

上图展示了执行过程。需要注意，不同数据库的架构并不相同，这张图展示的是一些常见设计。

## 第 1 步 - 传输层

SQL 语句通过传输层协议（例如 TCP）发送到数据库。

## 第 2 步 - 命令解析器

SQL 语句进入命令解析器，在这里进行语法和语义分析，随后生成查询树。

## 第 3 步 - 优化器

查询树会被送到优化器。优化器会生成执行计划。

## 第 4 步 - 执行器

执行计划会送到执行器。执行器从执行上下文中检索数据。

## 第 5 步 - 访问方法

访问方法提供执行所需的数据读取逻辑，从存储引擎中取出数据。

## 第 6 步 - Buffer Manager（只读查询）

访问方法会先判断 SQL 是否只读。如果是只读查询（SELECT 语句），它会交给 buffer manager 继续处理。buffer manager 会在缓存或数据文件中查找数据。

## 第 7 步 - 事务管理器（更新/插入）

如果语句是 UPDATE 或 INSERT，它会被送到事务管理器继续处理。

## 第 8 步 - 锁管理器

在事务期间，数据会处于锁定模式。这由锁管理器保证。它还会确保事务满足 ACID 特性。
