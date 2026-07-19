---
title: "数据库锁解释"
description: "了解不同类型的数据库锁及其作用。"
image: "https://assets.bytebytego.com/diagrams/0022-9-types-of-database-locks.png"
createdAt: "2024-03-10"
draft: false
categories:
  - database-and-storage
tags:
  - "Database Locking"
  - "Concurrency Control"
---

![](https://assets.bytebytego.com/diagrams/0022-9-types-of-database-locks.png)

在数据库管理中，锁是一种机制，用来防止对数据的并发访问失控，从而保证数据的完整性和一致性。

## 常见锁类型

下面是数据库中常用的几种锁：

* **共享锁（Shared Lock，S Lock）**

  它允许多个事务同时读取同一资源，但不能修改它。其他事务也可以对同一资源再获取共享锁。

* **排他锁（Exclusive Lock，X Lock）**

  它允许一个事务既读取又修改某一资源。在持有排他锁期间，其他事务不能再对同一资源获取任何类型的锁。

* **更新锁（Update Lock，U Lock）**

  它用于防止事务打算更新某资源时出现死锁场景。

* **模式锁（Schema Lock）**

  它用于保护数据库对象的结构。

* **批量更新锁（Bulk Update Lock，BU Lock）**

  它在批量插入操作中使用，通过减少所需锁数量来提升性能。

* **键范围锁（Key-Range Lock）**

  它用于索引数据，防止幻读（phantom reads），也就是防止有新行被插进事务已经读过的范围里。

* **行级锁（Row-Level Lock）**

  它锁定表中的某一行，同时允许其他行被并发访问。

* **页级锁（Page-Level Lock）**

  它锁定数据库中的某一页（一块固定大小的数据）。

* **表级锁（Table-Level Lock）**

  它锁定整张表。实现简单，但会显著降低并发度。
