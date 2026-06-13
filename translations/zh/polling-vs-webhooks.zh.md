---
title: "轮询与 Webhook"
description: "轮询与 Webhook：两种数据获取方式的详细对比。"
image: 'https://assets.bytebytego.com/diagrams/0057-pooling-vs-webhook.png'
createdAt: '2024-03-03'
draft: false
categories:
  - api-web-development
tags:
  - APIs
  - Webhooks
---

![](https://assets.bytebytego.com/diagrams/0057-pooling-vs-webhook.png)

## 轮询

轮询指的是以固定时间间隔反复检查外部服务或端点，以获取更新后的信息。

这就像不断询问：“你这里有新的东西给我吗？” 即使可能并没有任何更新。

这种方式资源消耗较大，也比较低效。

此外，你只有在主动询问时才能获得更新，因此可能错过真正实时的信息。

不过，开发者可以更好地控制何时以及如何获取数据。

## Webhook

Webhook 就像内置的通知系统。

你不需要持续询问信息。

相反，你会在自己的应用服务器中创建一个端点，并把它作为回调地址提供给外部服务，例如支付处理方或物流供应商。

每当有重要事件发生，外部服务就会调用这个端点，并提供相关信息。

这使得 Webhook 非常适合处理实时更新，因为一旦数据可用，它就会被推送到你的应用。

那么什么时候使用轮询，什么时候使用 Webhook？

当存在某些基础设施限制，无法使用 Webhook 时，轮询是一个可靠选择。另外，Webhook 存在由于网络问题而错过通知的风险，因此需要合适的重试机制。

对于需要即时数据投递的应用，推荐使用 Webhook。尤其是在高吞吐环境中，Webhook 在资源利用方面也更高效。
