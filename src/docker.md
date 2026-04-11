# docker 技术总结

## 职责定位

`docker/` 目录提供数据库、缓存、后端、前端的容器化部署方案，覆盖基础服务、开发环境与生产环境三类场景。

## 主要文件

| 文件 | 作用 |
| --- | --- |
| `docker-compose.base.yml` | 仅启动 PostgreSQL 与 Redis，适合本机直跑后端 |
| `docker-compose.dev.yml` | 开发环境容器编排 |
| `docker-compose.prod.yml` | 生产环境编排，包含 Nginx 前端与 Gunicorn 后端 |
| `backend/Dockerfile` | Django 镜像构建 |
| `backend/entrypoint.sh` | 后端启动前置逻辑 |
| `frontend/Dockerfile` | 前端静态站点构建 |
| `frontend/nginx.conf` | Nginx 站点配置 |
| `start-*.sh` | 基础、开发、生产环境启动脚本 |

## 技术要点

- 基础环境只暴露 PostgreSQL 和 Redis，本地开发最快。
- 生产环境通过 `.env` 注入机密，并强制要求 `DJANGO_SECRET_KEY` 存在。
- 生产编排中后端使用服务名 `postgres`、`redis` 作为容器内主机名。
- 前端容器只暴露 HTTP 端口，后端不直接向主机暴露端口，符合典型反向代理拓扑。
- 数据通过 volume 持久化，避免容器重建导致状态丢失。

## 运维提示

- 本目录的文档与脚本明确区分“本机开发基线”和“容器联调基线”，这是项目运行稳定性的关键。
- 生产启动必须带 `--env-file ../.env`，否则变量插值可能为空。
