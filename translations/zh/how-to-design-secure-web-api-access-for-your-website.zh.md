---
title: 如何设计安全的 Web API 访问
description: 学习如何为你的网站设计安全的 Web API 访问。
image: 'https://assets.bytebytego.com/diagrams/0325-secure-api.png'
createdAt: '2024-03-06'
draft: false
categories:
  - api-web-development
tags:
  - API Security
  - Authentication
---

![](https://assets.bytebytego.com/diagrams/0325-secure-api.png)

当我们向用户开放 Web API 访问时，需要确保每一次 API 调用都经过认证。这意味着用户必须是他们声称的那个人。

在这篇文章中，我们会探索两种常见方式：

* 基于 Token 的认证
* HMAC（基于哈希的消息认证码）认证

上图展示了它们的工作方式。

**基于 Token**

第 1 步：用户在客户端输入密码，客户端把密码发送给认证服务器。

第 2 步：认证服务器验证凭证，并生成一个带有过期时间的 token。

第 3 和第 4 步：现在客户端可以把 token 放在 HTTP Header 中，发送请求来访问服务器资源。在 token 过期之前，这个访问都是有效的。

**基于 HMAC**

这种机制使用哈希函数（SHA256 或 MD5）生成消息认证码，也就是签名。

第 1 和第 2 步：服务器生成两个 key，一个是公开的 APP ID（公钥），另一个是 API Key（私钥）。

第 3 步：现在我们在客户端生成一个 HMAC 签名（hmac A）。这个签名会使用图中列出的一组属性生成。

第 4 步：客户端把 hmac A 放在 HTTP Header 中，发送请求来访问服务器资源。

第 5 步：服务器接收到请求，请求中包含请求数据和认证 Header。服务器从请求中提取必要属性，并使用存储在服务器端的 API Key 生成一个签名（hmac B）。

第 6 和第 7 步：服务器比较 hmac A（客户端生成）和 hmac B（服务器端生成）。如果二者匹配，就把请求的资源返回给客户端。
