---
title: "事件溯源系统设计中的差异"
description: "探讨事件溯源系统设计的细节及其好处。"
image: "https://assets.bytebytego.com/diagrams/0188-event-sourcing.jpeg"
createdAt: "2024-02-08"
draft: false
categories:
  - database-and-storage
tags:
  - "event sourcing"
  - "system design"
---

![](https://assets.bytebytego.com/diagrams/0188-event-sourcing.jpeg)

如何用事件溯源（event sourcing）范式设计系统？它和普通系统设计有什么不同？好处又是什么？我们会在这篇文章里讨论这些问题。

上图对比了普通 CRUD 系统设计与事件溯源系统设计。我们用一个可以下单并支付订单的电商系统，来说明事件溯源如何工作。

事件溯源范式用于设计具有确定性的系统。它改变了普通系统设计的哲学。
