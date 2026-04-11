# types 技术总结

## 职责定位

`frontend/src/types/` 用于补充第三方库或业务代码的 TypeScript 类型声明。

## 当前实现

| 文件 | 作用 |
| --- | --- |
| `turndown.d.ts` | 为 `turndown` 提供类型声明补充 |

## 技术要点

- 虽然目录很小，但它解决了第三方库类型不完整的问题。
- 该目录的存在说明前端已在实践 TypeScript 类型兜底，而不是完全放任 `any` 扩散。
