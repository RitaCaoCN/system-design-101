---
title: 'HTTP/1 -> HTTP/2 -> HTTP/3'
description: '探索 HTTP 的演进：从 HTTP/1 到最新的 HTTP/3。'
image: 'https://assets.bytebytego.com/diagrams/0101-http-1-http-2-http-3.png'
createdAt: '2024-03-02'
draft: false
categories:
  - api-web-development
tags:
  - HTTP
  - Protocols
---

![](https://assets.bytebytego.com/diagrams/0101-http-1-http-2-http-3.png)

HTTP/1 开始于 1996 年，第二年 HTTP/1.1 出现。2015 年，HTTP/2 出现；2019 年，我们有了 HTTP/3。

随着每一次迭代，协议都以新的、有趣的方式演进。

* **HTTP/1** 及其子版本引入了持久连接、流水线，以及 Header 的概念。这个协议构建在 TCP 之上，为万维网上的通信提供了一种可靠方式。尽管它已经有 25 年以上历史，今天仍然在使用。
* **HTTP/2** 带来了多路复用、流优先级、服务器推送和 HPACK 压缩等新特性。不过，它底层仍然使用 TCP。
* **HTTP/3** 使用 Google 的 QUIC，而 QUIC 构建在 UDP 之上。换句话说，HTTP/3 已经离开了 TCP。
