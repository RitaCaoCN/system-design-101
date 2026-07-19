---
title: "数据库隔离级别"
description: "了解数据库隔离级别以及它们对事务并发的影响。"
image: "https://assets.bytebytego.com/diagrams/0239-isolation-level.png"
createdAt: "2024-02-03"
draft: false
categories:
  - database-and-storage
tags:
  - "Databases"
  - "Transactions"
---

![](https://assets.bytebytego.com/diagrams/0239-isolation-level.png)

## 它们是用来做什么的？

数据库隔离性让一个事务在执行时，可以表现得像系统中没有其他并发运行的事务一样。

上图展示了四种隔离级别。

## 隔离级别

* **Serializable（可串行化）**：这是最高的隔离级别。并发事务会被保证按顺序执行。

* **Repeatable Read（可重复读）**：事务中读取到的数据，会保持为事务开始时看到的状态。

* **Read Committed（读已提交）**：只有在事务提交之后，其他事务才能读到它对数据的修改。

* **Read Uncommitted（读未提交）**：一个事务还没提交时，其他事务就可能读到它做出的数据修改。

隔离性通常由 MVCC（多版本并发控制）和锁来保证。

## MVCC 示例

图中以 **Repeatable Read（可重复读）** 为例，说明 MVCC 是如何工作的：

每一行记录都有两个隐藏字段：`transaction_id` 和 `roll_pointer`。当事务 A 启动时，会创建一个新的 Read View，此时 `transaction_id=201`。紧接着事务 B 启动，又创建一个新的 Read View，此时 `transaction_id=202`。

现在事务 A 把余额修改为 200，于是会生成一条新的日志记录，`roll_pointer` 指向旧记录。此时事务 A 还没有提交，而事务 B 去读取余额。事务 B 发现 `transaction_id=201` 对应的事务尚未提交，于是会继续读取下一条已提交的记录，也就是 `transaction_id=200` 的那条记录。

即使事务 A 之后提交了，事务 B 仍然会按照它启动时创建的 Read View 来读取数据。因此，事务 B 始终看到的余额都是 `100`。
