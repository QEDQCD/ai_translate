# users 技术总结

## 职责定位

`apps/users/` 负责系统级能力，包括认证、用户管理、租户与部门、角色权限、系统配置、系统消息，以及与 Redis/短信/微信相关的接入。

## 核心文件

| 文件 | 作用 |
| --- | --- |
| `models.py` | 用户、角色、租户、部门、系统配置、系统消息等模型 |
| `views.py` | 注册、登录、个人信息、租户切换、部门管理等 API |
| `authentication.py` | Bearer Token 认证 |
| `middleware.py` | `TenantMiddleware`，将租户上下文注入请求 |
| `permissions.py` | RBAC 与租户权限检查工具 |
| `backends.py` | 自定义认证后端 |
| `redis_client.py` | 验证码、票据、登录失败次数等 Redis 存取 |
| `sms_service.py` / `wechat_oauth.py` | 短信与微信登录接入 |

## 技术要点

- 用户模型为了兼容历史表结构，保留了较多原始 SQL 操作，而不是纯 Django ORM。
- 登录同时兼容手机号密码、手机号验证码、旧用户名密码模式。
- 租户体系通过 `Team`、`TeamMember`、`current_tenant`、`default_tenant` 实现多租户切换。
- `permissions.py` 同时提供装饰器、查询过滤与实例赋租户工具，给业务应用复用。
- 管理命令覆盖管理员初始化、系统配置初始化、登录修复、示例爬虫配置等场景。

## 设计特征

- 更偏“平台底座”角色，而不是单纯用户应用。
- 强依赖 Redis，可在 Redis 不可用时回退到内存存储，增强开发环境容错。
- 系统级配置与系统消息也归属本目录，说明该模块同时承担平台控制台职责。
