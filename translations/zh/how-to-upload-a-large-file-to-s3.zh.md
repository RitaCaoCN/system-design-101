---
title: "如何把大文件上传到 S3"
description: "优化向 S3 这类对象存储上传大文件时的性能。"
image: "https://assets.bytebytego.com/diagrams/0284-multipart-upload.png"
createdAt: "2024-01-30"
draft: false
categories:
  - database-and-storage
tags:
  - "S3"
  - "Object Storage"
---

![](https://assets.bytebytego.com/diagrams/0284-multipart-upload.png)

我们该如何在把大文件上传到 S3 这类对象存储时，优化上传性能？

在回答这个问题前，先看看为什么要优化这个过程。有些文件可能大到几个 GB。虽然可以直接上传这么大的对象，但耗时会很长。如果上传中途网络断了，就得重新来过。更好的办法，是把大文件切成更小的部分，分别上传。等所有分片都上传完后，对象存储再把这些分片重新组装成完整对象。这个过程叫做 **分段上传**（multipart upload）。

上图展示了分段上传的工作方式：

1. 客户端先调用对象存储，发起一次分段上传。

2. 数据存储返回一个 `uploadID`，用来唯一标识这次上传。

3. 客户端把大文件切成多个小对象并开始上传。假设文件大小是 1.6GB，客户端把它切成 8 份，那么每份就是 200MB。客户端把第一份连同第 2 步拿到的 `uploadID` 一起上传到数据存储。

4. 每上传完一份，数据存储都会返回一个 `ETag`，本质上就是这份内容的 md5 校验值。它用于验证分段上传是否正确。

5. 当所有分片都上传完后，客户端发送一个 complete multipart upload 请求，其中包含 `uploadID`、分片编号和各个 `ETag`。

6. 数据存储根据分片编号把对象重新组装起来。因为对象很大，这一步可能会持续几分钟。组装完成后，系统会返回成功消息给客户端。
