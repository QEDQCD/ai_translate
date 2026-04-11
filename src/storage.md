# storage 技术总结

## 职责定位

`crawler_agent/storage/` 提供 Agent 的本地持久化能力，用于保存原始响应、采集元数据和推送状态。

## 主要文件

| 文件 | 作用 |
| --- | --- |
| `file_store.py` | 原始抓取结果落盘 |
| `sqlite_store.py` | SQLite 元数据与推送状态管理 |

## 技术要点

- 本地存储层使 Agent 支持断点续推、失败重放和增量同步。
- `sqlite_store.py` 与 `content_hash` 机制配合后，能够避免重复推送未变化内容。
- 把落盘与抓取/推送解耦，有利于后续扩展更多本地缓存策略。
