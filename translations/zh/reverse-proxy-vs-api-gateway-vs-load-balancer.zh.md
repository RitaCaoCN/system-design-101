---
title: '反向代理、API 网关与负载均衡器'
description: '理解反向代理、API 网关和负载均衡器之间的区别。'
image: 'https://assets.bytebytego.com/diagrams/0320-reverse-gateway-lb.png'
createdAt: '2024-02-09'
draft: false
categories:
  - api-web-development
tags:
  - API Gateway
  - Load Balancing
---

![](https://assets.bytebytego.com/diagrams/0320-reverse-gateway-lb.png)

现代网站和应用常常非常繁忙，因此我们会使用各种工具来管理流量。这里我们介绍三个核心工具：反向代理、API 网关和负载均衡器。

* **反向代理：改变身份**
  * 它替服务器悄悄获取数据，同时隐藏真实服务器。
  * 很适合保护敏感网站，让它们免受网络攻击和窥探。
* **API 网关：请求投递员**
  * 它把请求投递到正确的服务。
  * 很适合拥有大量相互通信服务的繁忙应用。
* **负载均衡器：交通指挥员**
  * 它把流量均匀分发到多台服务器，避免瓶颈。
  * 对高流量、高需求的热门网站来说非常关键。

简单来说，如果你需要隐藏和保护后端，选择反向代理；如果你需要组织服务间通信，选择 API 网关；如果你需要控制流量分发，选择负载均衡器。有时候，同时使用三者是明智的选择，它们可以一起让系统更安全、更高效。
