---
title: 什么是 gRPC？
description: 了解 gRPC，一个由 Google 开发的高性能 RPC 框架。
image: 'https://assets.bytebytego.com/diagrams/0054-what-is-grpc.png'
createdAt: '2024-03-08'
draft: false
categories:
  - api-web-development
tags:
  - gRPC
  - Microservices
---

![](https://assets.bytebytego.com/diagrams/0054-what-is-grpc.png)

gRPC 是一个高性能、开源、通用的 RPC（远程过程调用）框架，最初由 Google 开发。它使用 HTTP/2 作为传输协议，使用 Protocol Buffers 作为接口描述语言，并提供认证、负载均衡等能力。

gRPC 旨在让微服务架构中的服务之间能够高效、可靠地通信，因此它是构建分布式系统和 API 的常见选择。

**gRPC 的核心特性：**

* **Protocol Buffers：** 默认情况下，gRPC 使用 Protocol Buffers，也就是 proto 文件，作为接口定义语言（IDL）。与 JSON 或 XML 相比，这会让 gRPC 消息更小、更快。
* **基于 HTTP/2 的传输：** gRPC 使用 HTTP/2 进行传输，相比 HTTP/1.x 可以带来许多改进。
* **多语言支持：** gRPC 支持大量编程语言。
* **双向流式通信：** gRPC 支持请求和响应的流式传输，因此可以开发复杂的实时应用，例如支持双向通信的聊天服务。
