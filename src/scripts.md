# scripts 技术总结

## 职责定位

`scripts/` 存放本地开发和演示脚本，主要面向 Windows/PowerShell 场景。

## 主要脚本

| 脚本 | 作用 |
| --- | --- |
| `dev.ps1` | 一键启动本地开发环境 |
| `stop.ps1` | 停止本地开发环境 |
| `config_llm.ps1` | 配置 LLM 相关环境 |
| `demo_crawler_config_center.ps1` | 演示 Agent 配置中心模式 |
| `demo_crawler_nasa.ps1` | 演示采集 Agent 抓取示例站点 |

## 技术要点

- 脚本目录偏“开发体验增强”，不直接承载业务逻辑。
- 从脚本内容和命名看，项目兼顾日常开发与方案演示两类使用场景。
- 若团队后续强化 CI/CD，可考虑把脚本能力进一步迁移到跨平台 Makefile 或 task runner。
