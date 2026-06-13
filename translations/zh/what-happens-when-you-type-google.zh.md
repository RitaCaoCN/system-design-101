---
title: "在浏览器输入 google.com 后会发生什么？"
description: "探索在浏览器输入 google.com 后，请求经历的完整旅程。"
image: "https://assets.bytebytego.com/diagrams/0410-what-happens-when-you-type-google-in-your-browser.png"
createdAt: "2024-03-12"
draft: false
categories:
  - technical-interviews
tags:
  - "Networking"
  - "Web Browsers"
---

![在浏览器输入 google.com 后会发生什么？](https://assets.bytebytego.com/diagrams/0410-what-happens-when-you-type-google-in-your-browser.png)

1. 首先，你在浏览器地址栏中输入网站地址。

2. 浏览器会先检查自己的缓存。如果缓存未命中，它就必须找到该域名对应的 IP 地址。

3. DNS 查询开始。你可以把它理解成查电话号码。请求会经过不同的 DNS 服务器，包括根 DNS 服务器、顶级域 DNS 服务器，以及权威 DNS 服务器。最后，浏览器会拿到 IP 地址。

4. 接下来，浏览器会发起 TCP 连接，这有点像一次握手。例如在 HTTP/1.1 的情况下，客户端和服务器会通过 SYN、SYN-ACK、ACK 消息完成 TCP 三次握手。

5. 握手成功后，浏览器向服务器发送 HTTP 请求，服务器返回 HTML、CSS 和 JS 文件。

6. 最后，浏览器开始处理这些内容。它会解析 HTML 文档，并创建 DOM 树和 CSSOM 树。

7. 浏览器执行 JavaScript，并通过多个步骤渲染页面，包括分词器、解析器、渲染树、布局和绘制。

8. 最终，网页出现在你的屏幕上。
