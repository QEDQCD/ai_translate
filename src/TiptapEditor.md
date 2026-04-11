# TiptapEditor 技术总结

## 职责定位

`frontend/src/components/TiptapEditor/` 封装基于 Tiptap 的富文本编辑器，用于富文本录入、差异展示和格式控制。

## 主要内容

| 文件 | 作用 |
| --- | --- |
| `index.vue` | 编辑器主体 |
| `ToolBar.vue` | 工具栏 |
| `extensions/BackgroundColor.ts` | 背景色扩展 |
| `extensions/FontSize.ts` | 字号扩展 |
| `extensions/DiffBlock.ts` | 差异块扩展，适合翻译对比场景 |

## 技术要点

- 扩展点清晰，说明编辑器不是纯第三方组件接入，而是围绕业务做过二次开发。
- `DiffBlock` 说明系统存在“原文/译文差异呈现”诉求。
- 与 Markdown、HTML 差异工具配合后，可形成完整的内容校对工作流。
