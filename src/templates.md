# templates 技术总结

## 职责定位

`templates/` 目录用于后端渲染模板，目前主要承担单页应用生产模式的壳页输出。

## 当前实现

| 文件 | 作用 |
| --- | --- |
| `index.html` | 生产模式下的 SPA 模板入口 |

## 技术要点

- `backend/urls.py` 中的 `spa_fallback_view` 会在非 API 路径下渲染这里的模板。
- 模板目录虽然很轻，但它是 Django 与前端构建产物衔接的关键一环。
