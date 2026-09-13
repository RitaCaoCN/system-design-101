# Translate Cache And Database Guides Implementation Plan

> **For Agent:** REQUIRED SKILL: subagent-driven-development to implement this plan task-by-task.

**Goal:** Translate all untranslated guides under the `缓存与性能` and `数据库与存储` sections into Chinese files under `translations/zh/`, and track every target file in this plan as a todo item.

**Architecture:** Reuse the repository's existing translation convention: one Chinese Markdown file per guide in `translations/zh/`, named `<slug>.zh.md`, preserving frontmatter shape, image links, heading structure, and list formatting. Execute the work in section-sized batches, verify the source file exists before translation, and confirm the translated file is created at the expected target path.

**Tech Stack:** Markdown, frontmatter, repository guide sources under `data/guides/`, translated outputs under `translations/zh/`.

---

## Bound Design / Discussion

- Discussion checklist: `docs/plans/2026-06-13-translation-next-study-discussion-checklist.md`

## Scope

- In scope:
  - All guides listed under `数据库与存储` in `translations/zh/README.zh.md`
  - All guides listed under `缓存与性能` in `translations/zh/README.zh.md`
  - New translated files in `translations/zh/*.zh.md`
  - This implementation plan as the todo tracker
- Out of scope:
  - Updating other sections in `translations/zh/README.zh.md`
  - Translating guides from other categories
  - Refactoring source English guides

## Preflight Evidence

| Check | Command | Expected | Observed | Exit code | Verdict |
| --- | --- | --- | --- | --- | --- |
| Plan path tracking | `git check-ignore -q docs/plans/2026-06-13-translate-cache-db-guides.md; echo $?` | `1` meaning the plan file is not ignored | `1` | `0` | pass |
| Source guide directory exists | `find data/guides -maxdepth 1 -type f | sed 's#data/guides/##' | sort` | Source guide files are present | Output listed repository guide source files including cache and database slugs | `0` | pass |
| Target translation directory exists | `find translations/zh -maxdepth 1 -type f | sed 's#translations/zh/##' | sort` | Existing translated files are present and naming convention is visible | Output listed existing `*.zh.md` files under `translations/zh/` | `0` | pass |
| Source-of-truth section inventory | `node -e '...extract 缓存与性能 + 数据库与存储 items from translations/zh/README.zh.md...'` | All target titles and slugs can be enumerated from the Chinese README | Output listed 76 title/slug pairs across the two sections | `0` | pass |

## Specification Closure

1. **External I/O unit**
   - One bounded operation is one source guide translated into one target file at `translations/zh/<slug>.zh.md`.
2. **Retry vs limit interaction**
   - No automatic retries are needed. If a source file is missing or malformed, stop that file, document the blocker, and continue with other independent files only after recording the issue.
3. **Single-knob vs internal workers**
   - There is no user-facing concurrency knob in this task. Work proceeds in section batches while keeping file naming and formatting consistent.
4. **Other backends**
   - Only local repository files are in scope. No external translation services, network APIs, or non-repo backends are used.
5. **Ordering / fairness**
   - Preserve the section order from `translations/zh/README.zh.md`. Within each section, translate files in listed order so the todo list matches progress naturally.
6. **Backpressure**
   - Because the batch is large, progress should be checkpointed by coherent groups of files. If the batch cannot be fully completed in one pass, preserve completed translations and leave remaining todo items unchecked.
7. **Acceptance**
   - A translation is accepted when the source English guide exists, the Chinese target file exists, frontmatter keys are preserved, body content is translated into readable Chinese, and a read-back command shows the created file content.
8. **Doc precedence**
   - `translations/zh/README.zh.md` is the authoritative inventory for which files belong to the two requested sections. Existing translated files in `translations/zh/` define naming and formatting conventions.

## Tasks

### Task 1: Maintain the translation todo tracker

**Files:**
- Create: `docs/plans/2026-06-13-translate-cache-db-guides.md`
- Reference: `docs/plans/2026-06-13-translation-next-study-discussion-checklist.md`

**Steps:**
1. Record the exact requested scope from the discussion checklist.
2. Enumerate every target guide from the two requested sections.
3. Keep each file as a markdown todo item in this plan.

Done when: the plan contains a complete ordered checklist for all target files plus acceptance notes.

### Task 2: Translate database-and-storage guides

**Files:**
- Modify/Create: `translations/zh/*.zh.md`
- Reference: `data/guides/*.md`

**Steps:**
1. Open each source file in `data/guides/` using the slug listed below.
2. Create the matching `translations/zh/<slug>.zh.md`.
3. Preserve frontmatter keys and image references while translating `title`, `description`, headings, bullets, and prose to Chinese.
4. Read back created files to verify formatting and content.

Done when: every database guide listed in the checklist below exists as a translated Chinese file.

### Task 3: Translate caching-performance guides

**Files:**
- Modify/Create: `translations/zh/*.zh.md`
- Reference: `data/guides/*.md`

**Steps:**
1. Open each source file in `data/guides/` using the slug listed below.
2. Create the matching `translations/zh/<slug>.zh.md`.
3. Preserve frontmatter keys and image references while translating `title`, `description`, headings, bullets, and prose to Chinese.
4. Read back created files to verify formatting and content.

Done when: every cache/performance guide listed in the checklist below exists as a translated Chinese file.

### Task 4: Verification pass

**Files:**
- Verify: `translations/zh/*.zh.md`

**Steps:**
1. Run a repository file listing to confirm all target files now exist.
2. Spot-check translated files from both sections with `sed -n` reads.
3. Run `git status --short` to confirm the created files are visible for review.

Done when: existence, readability, and repository status are all confirmed.

## Todo Checklist

### 数据库与存储

- [x] `translations/zh/read-replica-pattern.zh.md` - 读副本模式
- [x] `translations/zh/pessimistic-vs-optimistic-locking.zh.md` - 悲观锁与乐观锁
- [ ] `translations/zh/how-to-upload-a-large-file-to-s3.zh.md` - 如何把大文件上传到 S3
- [x] `translations/zh/types-of-message-queue.zh.md` - 消息队列类型
- [ ] `translations/zh/smooth-data-migration-with-avro.zh.md` - 用 Avro 实现平滑数据迁移
- [ ] `translations/zh/the-ultimate-kafka-101-you-cannot-miss.zh.md` - 终极 Kafka 101
- [x] `translations/zh/what-are-database-isolation-levels.zh.md` - 数据库隔离级别
- [ ] `translations/zh/how-do-we-manage-data.zh.md` - 6 个数据管理模式
- [ ] `translations/zh/why-is-kafka-fast.zh.md` - Kafka 为什么快？
- [ ] `translations/zh/explaining-the-4-most-commonly-used-types-of-queues-in-a-single-diagram.zh.md` - 4 种常用队列解释
- [ ] `translations/zh/time-series-db-tsdb-in-20-lines.zh.md` - 20 行解释时序数据库 TSDB
- [ ] `translations/zh/differences-in-event-sourcing-system-design.zh.md` - 事件溯源系统设计中的差异
- [ ] `translations/zh/erasure-coding.zh.md` - 纠删码
- [ ] `translations/zh/delivery-semantics.zh.md` - 交付语义
- [ ] `translations/zh/change-data-capture-key-to-leverage-real-time-data.zh.md` - 变更数据捕获：利用实时数据的关键
- [ ] `translations/zh/can-kafka-lose-messages.zh.md` - Kafka 会丢消息吗？
- [ ] `translations/zh/storage-systems-overview.zh.md` - 存储系统概览
- [ ] `translations/zh/explain-the-top-6-use-cases-of-object-stores.zh.md` - 对象存储的 6 个使用场景
- [ ] `translations/zh/top-eventual-consistency-patterns-you-must-know.zh.md` - 必须知道的最终一致性模式
- [ ] `translations/zh/b-tree-vs.zh.md` - B-Tree 与 LSM-Tree
- [ ] `translations/zh/how-do-you-decide-which-type-of-database-to-use.zh.md` - 如何决定使用哪类数据库
- [ ] `translations/zh/cloud-database-cheat-sheet.zh.md` - 云数据库速查表
- [ ] `translations/zh/types-of-memory.zh.md` - 内存类型
- [ ] `translations/zh/understanding-database-types.zh.md` - 理解数据库类型
- [ ] `translations/zh/top-4-data-sharding-algorithms-explained.zh.md` - 4 种数据分片算法
- [ ] `translations/zh/top-6-database-models.zh.md` - 6 种数据库模型
- [ ] `translations/zh/how-is-a-sql-statement-executed-in-the-database.zh.md` - SQL 语句在数据库中如何执行
- [ ] `translations/zh/what-is-serverless-db.zh.md` - 什么是 Serverless DB？
- [ ] `translations/zh/why-is-postgresql-voted-as-the-most-loved-database-by-stackoverflow-2022-developer-survey.zh.md` - PostgreSQL 为什么最受喜爱
- [ ] `translations/zh/top-10-most-popular-open-source-databases.zh.md` - 10 个最流行的开源数据库
- [ ] `translations/zh/is-postgresql-eating-the-database-world.zh.md` - PostgreSQL 正在吞噬数据库世界吗？
- [ ] `translations/zh/how-to-choose-the-right-database.zh.md` - 如何选择正确的数据库
- [ ] `translations/zh/iqiyi-database-selection-trees.zh.md` - 爱奇艺数据库选择树
- [ ] `translations/zh/8-data-structures-that-power-your-databases.zh.md` - 支撑数据库的 8 种数据结构
- [ ] `translations/zh/how-to-implement-read-replica-pattern.zh.md` - 如何实现读副本模式
- [x] `translations/zh/a-crash-course-in-database-sharding.zh.md` - 数据库分片速成课
- [ ] `translations/zh/how-do-message-queue-architectures-evolve.zh.md` - IBM MQ -> RabbitMQ -> Kafka -> Pulsar：消息队列演进
- [ ] `translations/zh/cap-theorem-one-of-the-most-misunderstood-terms.zh.md` - CAP 定理：最容易被误解的术语之一
- [x] `translations/zh/consistent-hashing.zh.md` - 一致性哈希解释
- [ ] `translations/zh/types-of-databases.zh.md` - 数据库类型
- [ ] `translations/zh/key-concepts-to-understand-database-sharding.zh.md` - 理解数据库分片的关键概念
- [ ] `translations/zh/what-are-the-differences-among-database-locks.zh.md` - 数据库锁解释
- [ ] `translations/zh/a-cheatsheet-on-database-performance.zh.md` - 数据库性能速查表
- [x] `translations/zh/what-does-acid-mean.zh.md` - ACID 是什么意思？
- [ ] `translations/zh/top-5-kafka-use-cases.zh.md` - Kafka 的 5 个主要使用场景
- [ ] `translations/zh/types-of-memory-and-storage.zh.md` - 内存和存储类型
- [x] `translations/zh/7-must-know-strategies-to-scale-your-database.zh.md` - 扩展数据库的 7 个必知策略

### 缓存与性能

- [x] `translations/zh/what-is-elk-stack-and-why-is-it-so-popular-for-log-management.zh.md` - 什么是 ELK Stack，为什么它很流行？
- [x] `translations/zh/why-are-content-delivery-networks-cdn-so-popular.zh.md` - CDN 为什么如此流行？
- [x] `translations/zh/how-do-big-keys-impact-redis-persistence.zh.md` - Redis 大 Key 如何影响持久化
- [x] `translations/zh/a-beginner's-guide-to-cdn-content-delivery-network.zh.md` - CDN 初学者指南
- [x] `translations/zh/the-ultimate-redis-101.zh.md` - 终极 Redis 101
- [x] `translations/zh/cache-systems-every-developer-should-know.zh.md` - 每个开发者都该了解的缓存系统
- [x] `translations/zh/top-5-strategies-to-reduce-latency.zh.md` - 降低延迟的 5 个策略
- [x] `translations/zh/top-5-caching-strategies.zh.md` - 5 个缓存策略
- [x] `translations/zh/things-to-consider-when-using-cache.zh.md` - 使用缓存时要考虑的事情
- [x] `translations/zh/most-popular-cache-eviction.zh.md` - 缓存淘汰策略
- [x] `translations/zh/memcached-vs-redis.zh.md` - Memcached 与 Redis
- [ ] `translations/zh/low-latency-stock-exchange.zh.md` - 低延迟证券交易所
- [ ] `translations/zh/cache-miss-attack.zh.md` - 缓存未命中攻击
- [ ] `translations/zh/top-8-cache-eviction-strategies.zh.md` - 8 个缓存淘汰策略
- [x] `translations/zh/how-can-cache-systems-go-wrong.zh.md` - 缓存系统可能如何出错？
- [ ] `translations/zh/top-6-elasticsearch-use-cases.zh.md` - Elasticsearch 的 6 个使用场景
- [ ] `translations/zh/how-does-cnd-work.zh.md` - CDN 如何工作？
- [ ] `translations/zh/how-redis-architecture-evolve.zh.md` - Redis 架构如何演进
- [ ] `translations/zh/how-does-redis-persist-data.zh.md` - Redis 如何持久化数据？
- [ ] `translations/zh/how-can-redis-be-used.zh.md` - Redis 可以如何使用？
- [x] `translations/zh/why-is-redis-so-fast.zh.md` - Redis 为什么这么快？
- [ ] `translations/zh/how-do-we-learn-elasticsearch.zh.md` - 如何学习 Elasticsearch
- [x] `translations/zh/what-is-cdn-content-delivery-network.zh.md` - 什么是 CDN？
- [ ] `translations/zh/how-to-load-your-websites-at-lightning-speed.zh.md` - 前端性能优化
- [ ] `translations/zh/which-latency-numbers-should-you-know.zh.md` - 你应该知道哪些延迟数字？
- [ ] `translations/zh/what-are-the-top-caching-strategies.zh.md` - 常见缓存策略
- [ ] `translations/zh/top-9-website-performance-metrics-you-cannot-ignore.zh.md` - 9 个网站性能指标
- [ ] `translations/zh/top-5-common-ways-to-improve-api-performance.zh.md` - 提升 API 性能的 5 种常见方式
- [x] `translations/zh/learn-cache.zh.md` - 学习缓存
