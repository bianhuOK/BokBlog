---
title: Elastic Search
date: 2025-04-20T21:10:00+08:00
updated: 2025-04-20T21:10:00+08:00
keywords: ["es", "test"]
featured: true
summary: "es基础概念和应用"
---
ES组件研究

> blog 编写线索
> 切入点：数据结构，底层工具，架构，架构延伸，

# 基础概念
## ES是什么?
> Elasticsearch is a distributed, open-source search and analytics engine built on Apache Lucene. Elasticsearch provides a distributed system on top of Lucene

## 常见一些概念
- 文档 / 索引 / 类型 / 字段
- 倒排索引 & 正排索引
- Mapping 和分析器（Analyzer）
- 分片与副本机制


# 应用场景
https://dev.to/wallacefreitas/unlocking-the-power-of-elasticsearch-top-use-cases-for-real-time-search-and-analytics-5fe3#:~:text=One%20of%20the%20primary%20use,error);
todo

# 如何工作的
## 索引结构深入
- 倒排索引的数据结构详解
- 写入流程（文档是如何被索引的）
- Lucene 在 ES 中的角色

沿着这个分词索引来进行探索
Consider two documents:

``` {"greeting": "Hello, WORLD"}
{"greeting": "Hello, Mate"}
After text analysis, the inverted index might look like this:

Token	Document IDs
hello	1, 2
world	1
mate	2
```
## 搜索流程
●搜索流程（如何根据查询条件找到文档）
●搜索的优化（如何优化搜索性能）

Term Dictionary 数据量很大 -> term index  构建term索引，具体term在磁盘 (仍然很抽象，这里其他人是如何来理解并实践，比如写代码来验证 ->  store fields ?  -> doc values (列字段存储doc, 方便进行排序，聚合
```
GET /products/_search
{
  "sort": [
    { "price": "asc" }
  ]
}
```
  



# 有哪些启发

todo

# 参考资料
- https://mp.weixin.qq.com/s/IDQX8FMbLouh0DTod3XZVw
- https://medium.com/better-programming/system-design-series-elasticsearch-architecting-for-search-5d5e61360463

