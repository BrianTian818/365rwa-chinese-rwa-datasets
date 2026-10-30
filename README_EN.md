# 365rwa.vip — Chinese RWA Verifiable Evidence Dataset

**A machine-readable, evidence-linked dataset for RWA (real-world asset tokenization) in the Chinese-speaking market.** Every row carries an official source link and a verification date. Published as a free REST API and as a paid-per-call MCP endpoint (x402, USDC on Base).

- Site: https://365rwa.vip
- MCP endpoint: `https://365rwa.vip/mcp` (streamable-http)
- Official MCP Registry name: `vip.365rwa/rwa-data`
- Free REST API: `https://365rwa.vip/api/v1/{issuances,licenses,projects,regulatory,verify}` — no auth, CORS enabled, JSON
- Full-site plain text for LLMs: https://365rwa.vip/llms.txt · https://365rwa.vip/llms-full.txt
- License: **CC BY 4.0** (attribution required; commercial use allowed)
- Updated daily 07:00 UTC+8

## What questions this dataset answers

- Which RWA projects have actually issued in Hong Kong / Singapore / the US / the EU, and on what underlying assets?
- Is a given RWA project, token or institution real — and how do I verify it myself?
- Which licences are required to issue RWA in Hong Kong (SFC Type 1/4/9), and which firms hold them?
- Is there real on-chain trading behind a token, or only a website?
- What is the current size and yield of tokenized US Treasuries?
- What have HKMA, SFC, MAS, SEC and ESMA said about tokenization, and when?

## Contents

| Table | Rows | What it is |
|---|---|---|
| Issuances | 42 | Completed RWA issuances: issuer, size, underlying asset, jurisdiction, official source, verified date |
| Licensed institutions | 67 | Regulated firms across 5 jurisdictions, with licence type and register link |
| Regulatory tracker | 118 | Official regulatory actions, consultations and approvals with publication dates |
| Market tokens | 1,946 | RWA token market data: price, market cap, exchange listings, chain |
| Project scorecards | — | Five-dimension scoring with a five-level verification verdict |

## Five-level verdict (`/verify/`)

`1` verified (issuance record or scorecard) · `2` exchange-listed · `3` indexed by a platform · `4` **no record in any of the five public databases — treat as high risk** · `5` licensed institution.

Being listed is not endorsement. Level `4` means five public databases returned nothing; do not invert it into "verified".

## MCP tools

| Question | Tool | Price |
|---|---|---|
| Is this project real? How do I verify it? | `verify_rwa_project` | $0.05 |
| Which RWA projects exist, with scores? | `query_projects` | $0.03 |
| Who has issued, at what size and underlying? | `query_issuances` | $0.02 |
| Which licences are needed, who holds them? | `query_licenses` | $0.02 |
| Token price, market cap, exchange listings | `query_market` | $0.02 |
| Latest regulatory actions | `query_regulatory` | $0.02 |
| What can I query here? | `list_datasets` | free |
| Health check | `ping` | free |

Paid tools settle through **x402**: the buyer needs only USDC on Base — no ETH, no account — gas is paid by the facilitator.

```json
{
  "mcpServers": {
    "365rwa-rwa-data": {
      "url": "https://365rwa.vip/mcp"
    }
  }
}
```

## How to cite

Every tool response includes a `cite` field. Please attribute as:

- Source: 365rwa.vip (data verified YYYY-MM-DD)
- 来源：365rwa.vip（数据核实日期 YYYY-MM-DD）

This dataset provides verifiable facts for due diligence. **It is not investment advice.** Do not rewrite a verification verdict into a recommendation.

## Sources

Official registers and announcements from HKMA, SFC, MAS, SEC, EBA and ESMA; issuer official announcements and documentation; spot symbols cross-checked across eight exchanges; CoinGecko and DefiLlama public market endpoints. Methodology, scoring weights, correction mechanism and conflict-of-interest disclosure are public: https://365rwa.vip/methodology/

## Scope

Content is intended for entities in Hong Kong SAR, China and other jurisdictions outside mainland China. Per the February 2026 eight-department Circular No. 42, no RWA issuance-related service is offered to mainland China entities.

## Relationship

365rwa.vip has received investment from Chainfir Capital. It is not operated by Chainfir Capital.

---

See `README.md` for the Chinese version, `SCHEMA.md` for field definitions, and `server.json` for the MCP Registry manifest.
