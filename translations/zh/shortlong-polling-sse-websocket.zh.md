---
title: '短轮询、长轮询、SSE、WebSocket'
description: '了解实时 Web 更新：轮询、SSE 和 WebSocket。'
image: 'https://assets.bytebytego.com/diagrams/0337-short-long-polling-sse-websocket.jpeg'
createdAt: '2024-01-25'
draft: false
categories:
  - api-web-development
tags:
  - WebSockets
  - SSE
---

![](https://assets.bytebytego.com/diagrams/0337-short-long-polling-sse-websocket.jpeg)

HTTP 服务器不能自动向浏览器发起连接。因此，Web 浏览器才是连接的发起方。那么，如果我们想从 HTTP 服务器获得实时更新，接下来应该怎么做？

Web 浏览器和 HTTP 服务器都可以在这个任务中承担职责。

* **Web 浏览器承担主要工作**：短轮询或长轮询。短轮询中，浏览器会不断重试，直到拿到最新数据。长轮询中，HTTP 服务器在新数据到达之前不会返回结果。
* **HTTP 服务器和 Web 浏览器协作**：WebSocket 或 SSE（Server-Sent Events，服务器发送事件）。在这两种情况下，连接建立后，HTTP 服务器都可以直接向浏览器发送最新数据。区别在于，SSE 是单向的，因此浏览器不能通过同一连接向服务器发送新请求；而 WebSocket 是全双工的，因此浏览器可以持续发送新请求。
