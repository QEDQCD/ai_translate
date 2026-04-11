# frontend 技术总结

## 职责定位

`frontend/` 是基于 Vue 3 + Vite 的管理前端，承载情报工坊与系统管理两套工作台界面。

## 工程组成

| 位置 | 说明 |
| --- | --- |
| `package.json` | 前端依赖、Vite 脚本、编辑器与图表库配置 |
| `src/` | 业务源码主目录 |
| `dist/` | 构建产物目录，属于生成内容 |
| `MODULE_NAVIGATION.md` | 模块导航设计说明 |

## 技术栈

- 核心框架：Vue 3、Vue Router、Pinia
- 构建工具：Vite、TypeScript
- UI 组件：Element Plus
- 富文本与文档：Tiptap、Quill、html2canvas、jspdf、turndown、marked
- 可视化：ECharts

## 技术要点

- 前端将“情报工坊”和“系统”拆为两个一级模块，借助 Header + Sidebar 动态切换。
- 统一的 `shared/api.ts` 管理鉴权头、租户头、超时和错误提示。
- 多个页面围绕采集、翻译、导入导出、用户管理展开，属于典型中后台项目结构。
- 富文本、Markdown、HTML 差异比较工具较齐全，适合翻译结果校对与导出场景。
