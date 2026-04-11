# apps 技术总结

## 职责定位

`apps/` 是 Django 业务应用层，当前主要由 `users` 与 `data_collection` 两个核心应用组成，分别承载系统管理域与情报处理域。

## 关键内容

| 子目录 | 作用 |
| --- | --- |
| `users/` | 认证、用户、租户、RBAC、系统配置、系统消息 |
| `data_collection/` | 数据采集、翻译、导入导出、时间段、批次、任务管理 |

## 技术要点

- 两个应用都挂载在 `INSTALLED_APPS` 中，由 `backend/settings.py` 统一注册。
- 权限控制以 `apps.users` 为中心，业务模型通过 `tenant_id` 与请求上下文联动做隔离。
- API 路由在应用内定义，再由 `backend/urls.py` 按业务前缀聚合。
- `apps/` 层是业务实现主战场，模型、视图、命令、迁移基本都集中在这里。

## 交互关系

- `users` 向全局提供用户、租户、权限、认证中间件等底层能力。
- `data_collection` 依赖 `users` 的权限工具与租户隔离能力，完成采集到翻译再到导入导出的闭环。
