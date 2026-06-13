---
title: '关于 HTTP Header 的重要知识'
description: '了解客户端与服务器通信中的核心 HTTP Header。'
image: 'https://assets.bytebytego.com/diagrams/0231-http-header.png'
createdAt: '2024-01-30'
draft: false
categories:
  - api-web-development
tags:
  - HTTP
  - Headers
---

![](https://assets.bytebytego.com/diagrams/0231-http-header.png)

HTTP 请求就像向服务器索要某样东西，而 HTTP 响应就是服务器的回复。这有点像发送一条消息，然后收到一条回复。

HTTP 请求头是在发起请求时附带的额外信息，例如你正在发送什么类型的数据，或者你是谁。在响应头中，服务器会提供它返回响应的相关信息，例如你接收到的数据类型，或者是否有特殊指令。

在构建 RESTful 应用时，Header 在客户端与服务器通信中扮演着关键角色。为了在请求中发送正确的信息，并正确理解服务器的响应，你需要理解这些 Header。
