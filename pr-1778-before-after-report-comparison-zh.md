# PR #1778 前后报告对比（中文截图样例）

## 个股报告详情

- 修复前：报告详情只带行业排行时，Web 的“关联板块”只能给行业板块打上领涨/领跌信号；同名或独立的概念板块缺少概念排行来源，容易显示成普通标签。
- 修复后：`details.conceptRankings` 与 `details.sectorRankings` 分开透传，Web 按板块类型匹配排行；截图中“机器人概念”显示“领涨 +4.20%”，“芯片概念”显示“领跌 -2.05%”。
- 已验证截图：`pr-1778-stock-concept-boards-zh.png`。

## 大盘复盘报告

- 修复前：结构化大盘数据只展示行业板块排行，概念板块排行即使在后端 payload 中存在，也不会在 Web 大盘复盘视图里形成独立区域。
- 修复后：大盘复盘结构化数据同时展示“行业板块”和“概念板块”的领涨/领跌列表；截图中“机器人概念 +4.20%”与“转基因 -2.05%”作为概念板块单独展示。
- 已验证截图：`pr-1778-market-review-concepts-zh.png`。

## 实际验证说明

- 使用本地 Vite dev server（`http://127.0.0.1:5188/pr1778-evidence.html`）加载真实 `ReportOverview` 和 `MarketReviewReportView` 组件。
- Playwright 在截图前等待中文文本“机器人概念”“芯片概念”“概念板块”“转基因”和数值“+4.20%”可见。
- 截图样例使用中文报告语言（`reportLanguage: zh`）和中文样例数据。
