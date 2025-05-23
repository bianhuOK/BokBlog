---
title: 测试价值是什么
date: 2025-04-21T21:10:00+08:00
updated: 2025-04-21T21:10:00+08:00
keywords: ["test design", "test value"]
featured: true
summary: "探讨测试价值和测试质量体系建设"
---

# 测试价值是什么

> 好几次被问到这个问题了，但是总有些跟面试官理解不太一致的地方。

why? 为什么这个问题很重要？ 通过思考这个问题，能够指导我们做什么呢？ 测试工作会变得更好？ 测试方向会变得更有眼界？

**先不表** 让我好好酝酿酝酿。

我的回答： *测试价值是什么？测试价值是，确保产品需求满足用户场景，测试最重要的是什么，是保证交付质量*

其实，可以结合下面的测试质量体系建设的价值来说明。测试终极目标是保证好的交付质量，通过构建测试质量体系，能够让测试价值变得更加的清晰。

# 测试质量体系建设

> 怎么看待质量体系建设

> 体系为何物？ 房子蓝图，可以理解是组织，（延伸

**质量体系是一个系统化管理框架，能够有效覆盖质量目标，让产品符合用户和业务需求，它让测试价值不仅仅局限“找bug"而在于“防风险”；**

一个好的质量体系应该具备：

## 1. 全面性
- 覆盖产品规划（需求分析）到上线到售后的整个生命周期
- 开发阶段，监督代码规范，代码审查，单元测试
- 测试阶段，依据产品完成各种类型测试
- 上线阶段，要监控系统运行，收集反馈并处理

## 2. 可操作性
### 2.1 缺陷管理流程
- 从发现缺陷-记录缺陷-修复缺陷周期等

### 2.2 测试用例设计规范
- 好的测试方案模板
- 测试用例模板
- 自动化脚本协作管理

### 2.3 需求管理规范

### 2.4 回归规范
#### 环境准备
- 包括代码，部署，配置管理等
- 回归时间安排，一般安排在上线前两天

#### 回归测试策略
- 核心回归 + 部分回归
  - 核心用例回归
  - 本次版本的高优先级用例回归

#### 用例选取标准
- P0用例
- 异常测试
  - 参数边界
  - 模块接口超时
  - 重复
  - 中断等
- 兼容性测试
- 性能测试

#### 回归阶段常见问题
1. 新功能影响旧功能
   - 公共库改动导致其他模块出错
   - 权限改动导致出错
   - 资源占用问题
     - 例：CCTV模块上线，视频编码资源耗费高导致其他模块加载变慢
   - 网络请求频次影响

2. 数据交互问题
   - 多模块交互问题
   - 接口协议与版本兼容
     - 接口字段值枚举变化
     - PB字段增减处理

3. 性能问题
   - APP加载响应
   - 核心接口性能
   - 数据库连接数
   - 磁盘IO问题

#### 回归结果处理
- 输出清晰的回归结果报告
- 风险评估
- 问题影响分析

## 3. 可迭代性
- 引入新的测试技术（如流量回放）
- 改进缺陷管理流程
- 调整测试策略
  - 敏捷测试阶段：快速迭代，密切协作
  - 稳定阶段：推进自动化和专项测试
- 优化质量目标
  - 缺陷数量与线上逃逸率
  - 代码覆盖率 


# 未来测试规划

## v0
| 我回答希望将过去的功能和自动化测试经验应用到下一份工作，希望自己在5年内能够成为业务测试架构师。

未来的世界，重在系统设计，业务深度。传统的自动化编码，测试设计技巧，其实很容易被取代的。

- 这个问题让我对自身的职业产生了一些思考。
- 不局限于工作，我想赚钱，想更好的生活。
- 我当前的思维还是确定思维，在过往强烈的打工惯性下，怎么才能让自己成为一个“商人”， 去找价值大的东西，去想办法去接近它，去勇敢低尝试。

## v1

短期内，我希望能快速融入公司团队，熟悉业务流程和技术体系，通过高效完成测试任务、推动质量提升，为团队创造实际价值.

中长期来看，我希望成长为一名具备全局思维的资深测试工程师，不仅能独立负责复杂项目的测试工作，还能在自动化测试、CI/CD流程、质量体系建设这些方面具备更加专业的能力。


# 测试设计

｜ 测试分析能力真的很重要，至少我觉得我当前有所欠缺！

- 直接丢一个页面，进行测试设计
    - 比如说 港股交易的费用计算
- 直接说一个场景，进行测试设计
    - 比如购物车
    - 比如汇率换算

_到底怎么做好测试设计_

