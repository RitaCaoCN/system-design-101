---
title: 版本号是什么意思？
description: "理解版本号：MAJOR、MINOR、PATCH 和语义化版本。"
image: 'https://assets.bytebytego.com/diagrams/0415-what-do-version-numbers-mean.png'
createdAt: '2024-02-17'
draft: false
categories:
  - api-web-development
tags:
  - Versioning
  - SemVer
---

![](https://assets.bytebytego.com/diagrams/0415-what-do-version-numbers-mean.png)

语义化版本（Semantic Versioning，SemVer）是一种软件版本命名方案，目标是通过版本号传达一次发布中底层变更的含义。

* SemVer 使用三段式版本号：MAJOR.MINOR.PATCH。
  * **MAJOR 主版本号**：当存在不兼容的 API 变更时递增。
  * **MINOR 次版本号**：当以向后兼容的方式新增功能时递增。
  * **PATCH 补丁版本号**：当进行向后兼容的 bug 修复时递增。
* **示例工作流**
  * **初始开发阶段**
    * 从版本 0.1.0 开始。
  * **第一个稳定版本**
    * 达到稳定版本：1.0.0。
  * **后续变更**
    * **补丁发布**：1.0.0 需要修复一个 bug。更新到 1.0.1。
    * **次版本发布**：在 1.0.3 上新增一个向后兼容的功能。更新到 1.1.0。
    * **主版本发布**：在 1.2.2 中引入一个不向后兼容的重要变更。更新到 2.0.0。
  * **特殊版本和预发布版本**
    * **预发布版本**：1.0.0-alpha、1.0.0-beta、1.0.0-rc.1。
    * **构建元数据**：1.0.0+20130313144700。
