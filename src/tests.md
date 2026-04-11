# tests 技术总结

## 职责定位

`tests/` 目录存放 smoke test、样本数据和测试初始化代码，是更传统的测试资产目录。

## 主要内容

| 文件/子目录 | 作用 |
| --- | --- |
| `octoparse_api_smoke.py` | 八爪鱼接口连通性或基础行为验证 |
| `artifacts/` | 测试样本与工件，如 `octoparse_task_data.json` |
| `__init__.py` | 测试包初始化 |

## 技术要点

- 与 `test/` 目录相比，这里更偏测试数据与 smoke 用例沉淀。
- 同时存在 `test/` 与 `tests/`，说明仓库测试体系存在历史叠加，后续可逐步统一命名约定。
