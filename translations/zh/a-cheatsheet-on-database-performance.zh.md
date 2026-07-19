---
title: "数据库性能速查表"
description: "一份用关键策略优化数据库性能的简明指南。"
image: "https://assets.bytebytego.com/diagrams/0062-a-cheatsheet-on-database-performance.png"
createdAt: "2024-03-11"
draft: false
categories:
  - database-and-storage
tags:
  - "database"
  - "performance"
---

![](https://assets.bytebytego.com/diagrams/0062-a-cheatsheet-on-database-performance.png)

## 数据库性能速查表

下面是一份关于数据库性能的速查表：

### **1. 索引（Indexing）**

* **目的**：加快数据检索。
* **注意点**：
  * 索引过多会拖慢写入。
  * 定期检查并优化索引。

### **2. 查询优化（Query Optimization）**

* **技巧**：
  * 使用 `EXPLAIN` 分析查询计划。
  * 避免 `SELECT *`。
  * 写出高效的 `WHERE` 子句。

### **3. 连接池（Connection Pooling）**

* **好处**：
  * 减少反复建立新连接的开销。
  * 改善响应时间。

### **4. 缓存（Caching）**

* **层级**：
  * 应用层（例如 Memcached、Redis）。
  * 数据库层（查询缓存）。

### **5. 分片（Sharding）**

* **定义**：把数据分布到多个数据库中。
* **适用场景**：
  * 处理大数据集。
  * 提升写入性能。

### **6. 复制（Replication）**

* **类型**：
  * 主从（Master-slave）。
  * 双主（Master-master）。
* **目的**：
  * 读扩展。
  * 高可用。

### **7. 硬件（Hardware）**

* **注意点**：
  * 足够的内存。
  * 快速存储（SSD）。
  * 充足的 CPU。

### **8. 监控（Monitoring）**

* **指标**：
  * 查询响应时间。
  * CPU 使用率。
  * 磁盘 I/O。

### **9. 规范化 / 反规范化（Normalization / Denormalization）**

* **规范化**：减少冗余。
* **反规范化**：提升读性能（以冗余作为取舍）。

### **10. 分区（Partitioning）**

* **类型**：
  * 水平分区。
  * 垂直分区。
* **目的**：
  * 提升查询性能。
  * 让数据管理更容易。
