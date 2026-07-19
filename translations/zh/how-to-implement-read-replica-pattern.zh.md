---
title: "如何实现读副本模式"
description: "了解如何用数据库中间件实现读副本模式。"
image: "https://assets.bytebytego.com/diagrams/0162-database-middleware.png"
createdAt: "2024-03-03"
draft: false
categories:
  - database-and-storage
tags:
  - Database
  - Read Replicas
---

![](https://assets.bytebytego.com/diagrams/0162-database-middleware.png)

实现读副本模式通常有两种常见方式：

* 把路由逻辑嵌入应用代码中（上一篇文章已经解释过）。
* 使用数据库中间件。

这里我们重点看第二种方案。中间件在应用和数据库服务器之间提供透明路由。我们可以基于不同规则自定义路由逻辑，例如用户、schema、语句等。

上图展示了整体结构：

1. 当 Alice 在 amazon 上下单时，请求会发到 Order Service。
2. Order Service 并不直接访问数据库，而是把数据库查询发给数据库中间件。
3. 数据库中间件把写操作路由到主库。数据再复制到两个副本。
4. Alice 查看订单详情（读）。请求同样通过中间件发送。
5. Alice 查看最近的订单历史（读）。请求同样通过中间件发送。

数据库中间件充当应用和数据库之间的代理。它使用标准 MySQL 网络协议进行通信。

## 优点

* 简化应用代码。应用不需要了解数据库拓扑，也不必自己直接管理数据库访问。

* 兼容性更好。中间件使用 MySQL 网络协议。任何兼容 MySQL 的客户端都能轻松连上中间件。这让数据库迁移更容易。

## 缺点

* 增加系统复杂度。数据库中间件本身是一个复杂系统。由于所有数据库查询都要经过中间件，通常需要高可用部署，以避免单点故障。

* 额外的中间件层意味着额外的网络延迟。因此，这一层对性能要求很高。
