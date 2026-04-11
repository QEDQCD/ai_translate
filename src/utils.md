# utils 技术总结

## 职责定位

`frontend/src/utils/` 主要处理文本、HTML 与差异比对，是翻译校对和内容修订的重要支撑层。

## 主要文件

| 文件 | 作用 |
| --- | --- |
| `htmlDiff.ts` | HTML 差异计算 |
| `htmlStructureAnalyzer.ts` | HTML 结构分析 |
| `htmlTextReplace.ts` | HTML 文本替换 |
| `textDiff.ts` | 纯文本差异对比 |

## 技术要点

- 工具函数明显围绕“原文/译文对照”和“富文本修订”设计。
- 目录与 `TiptapEditor` 形成前后呼应，一个负责展示，一个负责算法处理。
- 说明该项目不只是展示翻译结果，还考虑了结果校验与内容编辑。
