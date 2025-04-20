---
title: mocker 设计开发
date: 2025-04-20T21:10:00+08:00
updated: 2025-04-20T21:10:00+08:00
keywords: ["mocker", "test"]
featured: true
summary: "这是一个mocker开发文档，包含本地和平台的系统设计"
---
# 背景目标

测试领域不可或缺的测试组件，能够构造制定第三方接口的返回结果，让开发更专注于自身业务逻辑代码。

## 背景

在微服务架构下，服务间的依赖关系复杂，导致：

- 联调测试需要多团队协调
- 第三方服务不可控（如支付接口）
- 异常场景难以模拟（如网络延迟、服务熔断）

## 开源mock库研究

- MockServer 
https://mock-server.com/
[MockServer 开源库研究](https://www.notion.so/MockServer-19c7c9e2d68a80249ba9f182f70cecc4?pvs=21)

- smoker
[smoker server ](https://www.notion.so/smoker-server-1a47c9e2d68a80d7b6c1d1ab7f38528a?pvs=21)

- wildmock 
[wire mock 研究](https://www.notion.so/wire-mock-1a47c9e2d68a800b8861d69b8844a3c8?pvs=21)
