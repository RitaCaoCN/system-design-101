---
title: "在浏览器输入 URL 后会发生什么？"
description: "探索一个 URL 从浏览器输入到网页展示的完整旅程。"
image: "https://assets.bytebytego.com/diagrams/0393-type-a-url-into-your-browser.png"
createdAt: "2024-03-13"
draft: false
categories:
  - technical-interviews
tags:
  - "Networking"
  - "Browsers"
---

![](https://assets.bytebytego.com/diagrams/0393-type-a-url-into-your-browser.png)

上图展示了整个过程的步骤。

- Bob 在浏览器中输入一个 URL，然后按下 Enter。在这个例子中，URL 由 4 个部分组成：
  - **scheme 协议方案** - *http://*。它告诉浏览器使用 HTTP 与服务器建立连接。
  - **domain 域名** - *example.com*。这是网站的域名。
  - **path 路径** - *product/electric*。这是服务器上请求资源所在的路径：phone。
  - **resource 资源** - *phone*。这是 Bob 想访问的资源名称。

- 浏览器会通过域名系统，也就是 DNS 查询，查找该域名对应的 IP 地址。为了让查询更快，数据会缓存在不同层级：浏览器缓存、操作系统缓存、本地网络缓存，以及 ISP 缓存。
  - 如果这些缓存中都找不到 IP 地址，浏览器就会去 DNS 服务器执行递归 DNS 查询，直到找到对应的 IP 地址为止。这个过程会在另一篇文章中介绍。

- 现在我们已经拿到了服务器的 IP 地址，浏览器会和服务器建立 TCP 连接。

- 浏览器向服务器发送 HTTP 请求。请求大致如下：

  ```
  GET /phone HTTP/1.1
  Host: example.com
  ```

- 服务器处理请求并返回响应。对于一次成功响应，状态码是 200。HTML 响应可能类似下面这样：

  ```
  HTTP/1.1 200 OK
  Date: Sun, 30 Jan 2022 00:01:01 GMT
  Server: Apache
  Content-Type: text/html; charset=utf-8

  <!DOCTYPE html>
  <html lang="en">
  Hello world
  </html>
  ```

- 浏览器渲染 HTML 内容。
