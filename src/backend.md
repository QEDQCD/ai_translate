# backend 技术总结

## 职责定位

`backend/` 是 Django 项目入口，负责全局配置、URL 聚合、WSGI/ASGI 启动与静态资源、SPA 回退策略。

## 核心文件

| 文件 | 作用 |
| --- | --- |
| `manage.py` | Django 管理命令入口 |
| `settings.py` | 环境变量加载、应用注册、中间件、数据库、Redis、LLM、微信等全局配置 |
| `urls.py` | 健康检查、认证、管理、采集、翻译、导入导出路由挂载 |
| `wsgi.py` / `asgi.py` | Web 服务入口 |

## 技术要点

- 优先从项目根目录 `.env` 加载配置，并兼容旧路径，降低部署迁移成本。
- `INSTALLED_APPS` 目前聚焦 `apps.users` 与 `apps.data_collection` 两个业务应用。
- 中间件中显式引入 `TenantMiddleware`，保证认证后可以注入租户上下文。
- `urls.py` 同时承担 SPA fallback，开发模式重定向到 Vite，生产模式返回模板页。
- 静态与媒体目录统一由 Django 暴露，生产可交由 Nginx 进一步接管。

## 对外接口边界

- `/api/auth/`：认证与系统管理域
- `/api/collection/`：采集域
- `/api/translation/`：翻译域
- `/api/import-export/`：导入导出域
- `/health`：健康检查
