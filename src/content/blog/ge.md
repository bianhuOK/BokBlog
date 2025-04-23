---
title: 大数据测试-great expectation
date: 2025-04-23T21:10:00+08:00
updated: 2025-04-23T21:10:00+08:00
keywords: ["test design", "gx"]
featured: true
summary: "dqc设置和设计方法"
---


# checkPoint

> 用于将数据验证的配置和操作封装成一个可重复执行的单元。它的核心作用是将 ​​数据验证（Expectations）​​ 和 ​​后续操作（Actions）​​ 组合在一起，实现自动化数据质量检查流程

---

**Checkpoint 的核心功能**
| 组件          | 作用                                                                                     | 示例                                                                 |
|---------------|----------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| 数据源     | 指定要验证的数据集（如数据库表、文件等）                                                 | `my_database_table` 或 `s3://my-bucket/data.csv`                   |
| 期望套件   | 定义具体的验证规则（Expectations），例如字段非空、唯一性、值范围等                       | 检查 `user_id` 是否唯一，`price` 是否在合理范围内                   |
| 验证操作   | 执行数据验证并生成结果报告                                                               | 运行验证后生成 JSON/HTML 报告                                       |
| 后续动作   | 根据验证结果触发操作（如发送通知、存储结果、中断流程等）                                  | 若验证失败，发送邮件告警；若成功，记录日志                           |

---

**Checkpoint 的典型应用场景**
1. 自动化数据管道验证  
   在 ETL/ELT 流程中插入 Checkpoint，确保数据在转换前后符合预期规则。  
   ```python
   checkpoint = SimpleCheckpoint(
       name="my_checkpoint",
       data_context=context,
       validations=[
           {"batch_request": batch_request, "expectation_suite_name": "my_suite"}
       ],
       action_list=[
           {"name": "store_validation_result"},
           {"name": "send_email_on_failure", "to": "team@example.com"}
       ]
   )
   checkpoint.run()
   ```

2. 监控数据质量波动  
   定期运行 Checkpoint，跟踪数据分布变化（如字段缺失率突增）。  
   ```yaml
   action_list:
     - name: store_evaluation_parameters
     - name: store_validation_result
     - name: update_data_docs
     - name: send_slack_notification_on_failure  # 失败时发送 Slack 告警
   ```

3. 版本化数据质量规则  
   将 Checkpoint 配置与期望套件（Expectation Suites）一同纳入版本控制，实现审计追踪。

---

**Checkpoint 配置的常见结构**
```yaml
name: my_checkpoint                # 检查点名称
config_version: 1.0                # 配置版本
module_name: great_expectations.checkpoint
class_name: SimpleCheckpoint
validations:
  - batch_request:                 # 要验证的数据批次
      datasource_name: my_datasource
      data_connector_name: default_inferred_data_connector_name
      data_asset_name: my_table
    expectation_suite_name: my_suite  # 关联的期望套件
action_list:                       # 验证后的操作链
  - name: store_validation_result
  - name: store_evaluation_params
  - name: update_data_docs         # 更新数据文档
  - name: send_email               # 邮件通知（需配置 SMTP）
    action:
      class_name: EmailAction
      notify_on: failure           # 仅在失败时发送
      to_emails: ["data-team@example.com"]
```

---

**Checkpoint 的关键优势**
1. 可复用性  
   一次定义，多次运行，避免重复配置验证规则。
2. 灵活触发  
   支持手动触发、调度器（如 Airflow）触发或 API 调用。
3. 结果可追溯  
   验证结果与数据文档（Data Docs）自动关联，便于回溯分析。

---

**Checkpoint vs. Expectation Suite**
|                | Checkpoint                          | Expectation Suite                     |
|----------------|-----------------------------------------|--------------------------------------------|
| 核心作用   | 执行验证流程（包含数据+规则+操作）         | 定义数据规则（如字段约束、业务逻辑）          |
| 依赖关系   | 依赖 Expectation Suite                  | 独立定义数据规则                             |
| 输出       | 验证结果、触发动作（如通知）              | 无直接输出，需通过 Checkpoint 执行           |

---

**实际使用中的注意事项**
1. 环境隔离  
   区分开发、测试、生产环境的 Checkpoint 配置，避免误操作。
2. 性能优化  
   大数据集验证时，通过抽样（Sampling）或增量检查提升效率。
3. 错误处理  
   在 `action_list` 中定义错误降级策略（如重试、日志记录）。

---

**总结**
Great Expectations 的 Checkpoint 是数据质量管理的“自动化执行引擎”，它将数据验证规则与运维操作紧密结合，帮助团队快速发现数据问题并响应，是构建健壮数据管道的关键工具。

