---
title: "悲观锁与乐观锁"
description: "了解悲观锁与乐观锁这两种保证数据一致性的策略。"
image: "https://assets.bytebytego.com/diagrams/0301-pessimistic-vs-optimistic-locking.png"
createdAt: "2024-01-29"
draft: false
categories:
  - database-and-storage
tags:
  - "Concurrency Control"
  - "Database Transactions"
---

![](https://assets.bytebytego.com/diagrams/0301-pessimistic-vs-optimistic-locking.png)

在多用户环境中，锁对于维护数据一致性和完整性非常重要。它可以防止多个用户同时修改同一份数据，从而避免出现数据不一致。

**悲观锁**假设冲突一定会发生，因此会在修改数据之前先把数据锁住。在锁被释放之前，其他用户不能访问或更新这份数据。

**乐观锁**则假设冲突比较少见。它允许多个用户同时访问数据，只在提交变更时检查是否发生冲突。如果检测到冲突，就回滚这次操作。

## 最佳实践

下面是一些值得注意的实践建议：

* 锁的持有时间应尽量短，以减少竞争。
* 锁的粒度应尽可能细，例如优先锁行而不是锁整张表。
* 对因冲突而失败的事务实现重试逻辑。
* 悲观锁更有利于保证数据完整性，但可能会影响性能。
* 乐观锁在效率和性能方面通常更有优势。
