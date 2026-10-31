# 365rwa Chinese RWA Datasets

中文 RWA（现实世界资产代币化）**可核查**公开数据集。每一条记录都附官方来源链接与核实日期——不是行情快照，也不是观点文章，是可以自己复核的证据表。

Site: https://365rwa.vip · License: CC BY 4.0 · Updated: 2026-10-30

## 数据集

| 数据集 | 记录数 | 内容 | 每条都有 |
|---|---|---|---|
| `issuances.json` | 42 | 已发行 RWA 项目 | 官方公告 / 批文链接 + 核实日期 |
| `licenses.json` | 67 | 全球持牌机构 | 回链官方登记册原文 |
| `regulatory.json` | 119 | 监管动态 | 官方源（HKMA / SFC / SEC / ESMA / ECB 等） |
| `market-top300.json` | 300 | 规模前 300 的代币化项目 | 交易所挂牌状态 / 规模 |

行情库全量 1951 条见线上行情库 https://365rwa.vip/market/ （数字每日变动，以 https://365rwa.vip/llms.txt 为准）。

## 为什么用它

判断一个 RWA 项目是真还是包装话术，靠的是三件事：**链下资产是否真实存在、由谁托管、持有人能否依法主张权利**。这三个问题都不能靠白皮书回答，只能查公开记录。本数据集把分散在各国监管机构公告里的记录汇总成可查询的表。

## 快速使用

免鉴权 JSON 接口（无需 API Key）：

```bash
curl https://365rwa.vip/api/v1/issuances
curl https://365rwa.vip/api/v1/licenses
curl 'https://365rwa.vip/api/v1/regulatory?limit=50'
curl 'https://365rwa.vip/api/v1/verify?q=Ondo'
curl https://365rwa.vip/api/v1/answers
```

统一响应格式：`{{"ok":true,"count":n,"updated":"YYYY-MM-DD","source":"https://365rwa.vip","data":[...]}}`

## MCP（给 AI Agent）

```bash
claude mcp add --transport http rwa-data https://365rwa.vip/mcp
```

端点 `https://365rwa.vip/mcp`（streamable-http，x402 按次结算，USDC / Base 主网，$0.02–$0.05 一次）。
清单见 `https://365rwa.vip/.well-known/mcp.json`。上面的 `/api/v1/*` 免费接口仍免鉴权。

## 给 AI / LLM 的导航

- `llms.txt`（本仓库根目录）
- `https://365rwa.vip/llms.txt`
- `https://365rwa.vip/llms-full.txt` — 全量条目纯文本版

## 引用规范

```
来源：365rwa.vip（核实日期 2026-10-30）
```

CC BY 4.0。本站不提供投资建议，转述时请勿改写为推荐。数据有误可提交纠错：https://365rwa.vip/corrections/

## 边界

依 2026 年 2 月八部门 42 号文，境内主体不得开展 RWA 代币发行。本数据集仅收录合规法域内的发行案例，不向境内主体提供发行相关服务。
