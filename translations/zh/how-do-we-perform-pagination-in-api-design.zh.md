---
title: API 设计中如何进行分页？
description: 了解 API 分页技术，以便高效获取数据。
image: 'https://assets.bytebytego.com/diagrams/0076-api-pagination-101.png'
createdAt: '2024-03-04'
draft: false
categories:
  - api-web-development
tags:
  - API Design
  - Pagination
---

![](https://assets.bytebytego.com/diagrams/0076-api-pagination-101.png)

在 API 设计中，分页对于高效处理大型数据集和提升性能非常关键。下面是六种常见的分页技术：

* **基于 Offset 的分页：**

  这种技术使用 offset 和 limit 参数来定义起始位置以及要返回的记录数量。

  * 示例：GET /orders?offset=0&limit=3
  * 优点：实现和理解都很简单。
  * 缺点：当 offset 很大时可能变得低效，因为数据库需要扫描并跳过许多行。

* **基于 Cursor 的分页：**

  这种技术使用 cursor，也就是一个唯一标识符，来标记数据集中的位置。通常，cursor 是一个编码后的字符串，指向某条具体记录。

  * 示例：GET /orders?cursor=xxx
  * 优点：对大型数据集更高效，因为不需要扫描被跳过的记录。
  * 缺点：实现和理解上稍微更复杂。

* **基于 Page 的分页：**

  这种技术指定页码和每页大小。

  * 示例：GET /items?page=2&size=3
  * 优点：容易实现和使用。
  * 缺点：当页码很大时，会出现类似基于 offset 分页的性能问题。

* **基于 Keyset 的分页：**

  这种技术使用某个 key 来过滤数据集，通常是主键或另一个有索引的列。

  * 示例：GET /items?after_id=102&limit=3
  * 优点：对大型数据集很高效，并且避免了大 offset 带来的性能问题。
  * 缺点：需要唯一且有索引的 key，实现起来可能比较复杂。

* **基于时间的分页：**

  这种技术使用时间戳或日期来分页浏览记录。

  * 示例：GET /items?start_time=xxx&end_time=yyy
  * 优点：适合按时间排序的数据集；如果新增记录进入数据集，也能确保不遗漏记录。
  * 缺点：需要可靠且一致的时间戳。

* **混合分页：**

  这种技术组合多种分页方式，以发挥各自优势。

  * 示例：组合 cursor 和基于时间的分页，以便高效滚动浏览按时间排序的记录。
  * 示例：GET /items?cursor=abc&start_time=xxx&end_time=yyy
  * 优点：可以为复杂数据集提供最佳性能和灵活性。
  * 缺点：实现更复杂，也需要谨慎设计。
