# data_collection 技术总结

## 职责定位

`apps/data_collection/` 是情报工坊业务核心，覆盖时间段管理、采集任务、原始数据、翻译配置与任务、导入导出批次等全链路能力。

## 核心文件

| 文件 | 作用 |
| --- | --- |
| `models.py` | 定义 `TimePeriod`、`CollectionTask`、`RawData`、`TranslationConfig`、`TranslationTask` 等模型 |
| `views.py` | 数据采集域 API，包括时间段、批次、推送、统计、采集任务 |
| `translation_views.py` | 翻译配置、任务、结果、LLM 状态、直接翻译 |
| `import_export_views.py` | 导入导出任务、批次、模板、文件下载 |
| `translation_executor.py` | 翻译任务入队与执行逻辑 |
| `import_export_executor.py` | 导入导出批处理执行逻辑 |
| `octoparse_client.py` / `octoparse_importer.py` | 外部采集源接入与导入 |
| `accuracy.py` / `translation_llm.py` | 内容质量与模型调用封装 |

## 业务模型

- `TimePeriod` 与 `TimePeriodStatistics`：按时间窗管理数据批次与统计口径。
- `CollectionTask`、`CollectionBatch`、`RawData`：采集任务、采集批次、原始内容数据。
- `TranslationConfig`、`TranslationTask`、`TranslationData`：翻译配置、任务执行与结果落库。
- `ImportExportBatch`、`ExportTimePeriod`、`ImportTimePeriod`：导入导出任务及与时间段的追溯关系。

## 技术要点

- API 统一使用 `tenant_id` 做租户过滤，个人模式通过 `tenant_id IS NULL` 区分。
- `push-data` 支持外部 Agent 直接推送数据，配合 `crawler-agent/config` 导出接口实现配置中心模式。
- 翻译能力内置语言归一化、语言推断、LLM 状态探测、BLBU 质量评估、低质量重试。
- 导入导出模块提供批次追踪、模板下载、失败记录导出，适合对账与回放。
- 迁移脚本较多，说明该模块迭代频繁，数据结构处于持续演进状态。

## 风险与观察

- `translation_views.py` 与 `import_export_views.py` 注释中仍保留“骨架”描述，说明部分接口曾按渐进式交付实现，后续维护需特别关注覆盖率。
- 模型较多且跨链路联动强，新增字段时必须同步考虑租户字段、列表筛选、统计口径和导入导出兼容性。
