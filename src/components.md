# components 技术总结

## 职责定位

`frontend/src/components/` 提供页面级通用组件，包括应用头部、侧边栏、租户切换器、Markdown 渲染器与富文本编辑器。

## 主要组件

| 组件 | 作用 |
| --- | --- |
| `AppHeader.vue` | 顶部导航，承载模块切换器与用户入口 |
| `AppSidebar.vue` | 侧边导航，根据模块与权限展示菜单 |
| `TenantSwitcher.vue` | 多租户切换入口 |
| `MarkdownRender.vue` | Markdown 内容渲染 |
| `TiptapEditor/` | 富文本编辑器及扩展 |

## 技术要点

- 组件目录承担全局导航职责，实际上是整个前端信息架构的控制面。
- 侧边栏与模块映射联动，体现“模块感知型导航”设计。
- 编辑器能力被独立拆分为子目录，方便承接翻译校对与内容编辑场景。
