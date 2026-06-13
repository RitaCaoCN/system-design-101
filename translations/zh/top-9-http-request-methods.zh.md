---
title: '9 个常见 HTTP 请求方法'
description: '用清晰解释了解 9 个常见 HTTP 请求方法。'
image: 'https://assets.bytebytego.com/diagrams/0371-top-9-http-request-methods.png'
createdAt: '2024-02-27'
draft: false
categories:
  - api-web-development
tags:
  - HTTP
  - API
---

![](https://assets.bytebytego.com/diagrams/0371-top-9-http-request-methods.png)

GET、POST、PUT……常见 HTTP “动词”可以用一张图来理解。

* **HTTP GET**

  从服务器获取资源。它是幂等的。多次发送相同请求，会返回相同结果。

* **HTTP PUT**

  更新或创建一个资源。它是幂等的。多次发送相同请求，会更新同一个资源。

* **HTTP POST**

  用于创建新资源。它不是幂等的，发送两次相同的 POST 请求会重复创建资源。

* **HTTP DELETE**

  用于删除资源。它是幂等的。多次发送相同请求，会删除同一个资源。

* **HTTP PATCH**

  PATCH 方法用于对资源进行局部修改。

* **HTTP HEAD**

  HEAD 方法请求一个与 GET 请求相同的响应，但不返回响应体。

* **HTTP CONNECT**

  CONNECT 方法会与目标资源标识的服务器建立一条隧道。

* **HTTP OPTIONS**

  OPTIONS 方法用于描述目标资源支持的通信选项。

* **HTTP TRACE**

  TRACE 方法会沿着到目标资源的路径执行一次消息回环测试。
