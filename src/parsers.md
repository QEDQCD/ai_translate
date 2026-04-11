# parsers 技术总结

## 职责定位

`crawler_agent/parsers/` 负责把不同来源的原始页面或订阅内容解析成统一数据项。

## 解析器组成

| 文件 | 作用 |
| --- | --- |
| `rss_parser.py` | RSS/Atom 订阅解析 |
| `single_page_parser.py` | 单页正文抽取与去噪 |
| `sitemap_parser.py` | Sitemap 与 sitemapindex 解析 |
| `html_list_parser.py` | HTML 列表页链接解析 |
| `text_utils.py` | 文本处理辅助 |
| `time_utils.py` | 时间字段解析辅助 |

## 技术要点

- 解析器已经覆盖多数内容站点的常见入口形式。
- `single_page_parser.py` 是质量关键点，直接影响后续翻译噪声水平。
- 时间与文本工具被拆出，说明解析过程已经考虑多站点、多格式兼容。
