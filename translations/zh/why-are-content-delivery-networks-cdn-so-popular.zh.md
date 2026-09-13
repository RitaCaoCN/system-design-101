---
title: "CDN 为什么如此流行？"
description: "了解 CDN 为何流行，以及它如何影响性能。"
image: "https://assets.bytebytego.com/diagrams/0420-why-cdns-are-so-popular.png"
createdAt: "2024-02-16"
draft: false
categories:
  - caching-performance
tags:
  - CDN
  - Performance
---

![](https://assets.bytebytego.com/diagrams/0420-why-cdns-are-so-popular.png)

预计到 2028 年，CDN 市场规模将接近 380 亿美元。Akamai、Cloudflare、Amazon CloudFront 等公司都在这一领域大力投入。

## CDN 的影响

CDN 能提升性能、提高可用性，并改善带宽成本。使用 CDN 后，延迟通常会明显下降。

## CDN 请求流程

DNS 解析完成后，用户设备会把内容请求发送到 CDN 边缘服务器。

*   边缘服务器先检查本地缓存。如果命中，就直接把内容返回给用户。

*   如果未命中，边缘服务器会把请求转发到源站（origin server）。

*   从源站拿到内容后，边缘服务器会在本地缓存一份，再返回给用户。

## CDN 的架构

CDN 架构通常包含这些组件：

*   **源站（Origin Server）：** 内容的主来源。

*   **边缘服务器（Edge Servers）：** 在全球各地缓存并向用户提供内容。

*   **DNS：** 把域名解析为离用户最近的边缘服务器 IP。

*   **控制面（Control Plane）：** 负责配置与管理边缘服务器。

## CDN 请求路由

*   **GSLB：** 根据地理邻近、服务器负载、网络状况等因素，把用户请求路由到合适的服务器。

*   **Anycast DNS：** 允许多台服务器共享同一 IP，帮助把流量路由到最近的数据中心。

*   **互联网交换中心（IXP）：** CDN 厂商会在主要 IXP 部署节点，以便直接与 ISP 及其他网络交换流量。

## 最佳实践

优化 CDN 性能的关键最佳实践，通常围绕安全、缓存优化和内容优化这几方面。
