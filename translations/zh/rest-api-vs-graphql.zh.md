---
title: 'REST API 与 GraphQL'
description: '了解 REST API 和 GraphQL 在 API 设计中的区别。'
image: 'https://assets.bytebytego.com/diagrams/0036-rest-vs-graphql.png'
createdAt: '2024-03-11'
draft: false
categories:
  - api-web-development
tags:
  - API
  - GraphQL
---

![](https://assets.bytebytego.com/diagrams/0036-rest-vs-graphql.png)

谈到 API 设计，REST 和 GraphQL 各有优势和弱点。

**REST**

* 使用 GET、POST、PUT、DELETE 等标准 HTTP 方法执行 CRUD 操作。
* 当你需要在不同服务或应用之间提供简单、统一的接口时，REST 很合适。
* 缓存策略比较容易实现。
* 缺点是，如果要从多个独立端点组装相关数据，可能需要多次往返请求。

**GraphQL**

* 为客户端提供一个统一端点，让客户端精确查询自己需要的数据。
* 客户端可以在嵌套查询中指定确切字段，服务器只返回包含这些字段的优化载荷。
* 支持用于修改数据的 Mutations，也支持用于实时通知的 Subscriptions。
* 非常适合聚合多个来源的数据，也适合前端需求快速变化的场景。
* 不过，它会把复杂度转移到客户端；如果没有做好防护，也可能允许滥用型查询。
* 缓存策略可能比 REST 更复杂。

REST 和 GraphQL 之间的最佳选择，取决于应用和开发团队的具体需求。GraphQL 适合复杂或频繁变化的前端需求，而 REST 更适合偏好简单、一致契约的应用。
