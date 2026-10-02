<p align="center"><img src="assets/logo.png" width="96" alt="esimoa"></p>

# esimoa MCP — travel eSIM comparison for AI assistants

Search and compare travel eSIM data plans from **[esimoa](https://www.esimoa.com)** inside Claude, ChatGPT, Gemini, Cursor and any MCP client: filter by country, trip length, data, local phone number, local or roaming network, several countries at once, budget, hotspot and 5G. Each plan comes with a link to its page on esimoa.com, where you review and buy it.

```
https://api.esimoa.com/mcp
```

Remote server · Streamable HTTP · **no sign-in, no API key needed** · MCP protocol 2024-11-05 to 2026-07-28 · listed in the [official MCP Registry](https://registry.modelcontextprotocol.io) as `com.esimoa/esim`.

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=esimoa&config=eyJ1cmwiOiJodHRwczovL2FwaS5lc2ltb2EuY29tL21jcCJ9) [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_esimoa-0098FF?logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=esimoa&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.esimoa.com%2Fmcp%22%7D)

## Connect

| Client | How |
|---|---|
| **Claude** (claude.ai, desktop, mobile) | Settings → Connectors → **Add custom connector** → name `esimoa`, URL `https://api.esimoa.com/mcp` |
| **Claude Code** | `claude mcp add --transport http esimoa https://api.esimoa.com/mcp` — or install the plugin: `/plugin marketplace add nbase-io/esimoa-mcp` then `/plugin install esimoa@esimoa` |
| **ChatGPT** | Settings → Apps / Connectors → Advanced → Developer mode → create a connector with the URL above (no authentication) |
| **Gemini CLI** | `gemini extensions install https://github.com/nbase-io/esimoa-mcp` |
| **Cursor** | Settings → MCP → Add new server → type `http`, URL above |
| **VS Code** (Copilot agent mode) | Command palette → *MCP: Add Server* → HTTP → URL above |
| **Grok · Perplexity · Le Chat · Manus · Genspark** | Add a custom/remote MCP connector with the URL above, authentication *none* |
| **stdio-only clients** | `npx -y mcp-remote https://api.esimoa.com/mcp` |

Generic JSON config:

```json
{
  "mcpServers": {
    "esimoa": { "type": "http", "url": "https://api.esimoa.com/mcp" }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `search_esims` | Search and compare plans. Filters: `country` (ISO code or name in any language) or `countries` (plans that work in all of them), `days`, `data_gb` / `max_data_gb`, `unlimited`, `data_type` (`daily` \| `total`), `local_number`, `network` (`local` \| `roaming`), `multi_country`, `min_price_krw` / `max_price_krw`, `provider`, `hotspot`, `five_g`. Sort: `recommended`, `price`, `data`, `price_per_gb`, `validity`. |
| `get_esim` | Details of one plan: data, validity, coverage countries, hotspot, network, provider, local number, link. |
| `compare_esims` | Compare 2–5 plans side by side (ids from `search_esims`): price, data, validity, price per GB, coverage, network, hotspot, local number — and which has the lowest price, most data, longest validity and lowest price per GB. |
| `list_countries` | Destinations with plan counts and lowest prices. |
| `search` / `fetch` | Free-text search and document fetch (ChatGPT deep research format). Understands "unlimited", "daily", "local phone number", "local network", "hotspot", "5G". |

All tools are read-only. Prices are in KRW. Results come in 13 languages (`lang`: ko, en, ja, zh-CN, zh-TW, es, fr, ar, vi, th, id, it, de). The tools never take payment or create orders, and they cannot see your esimoa account (orders, installed eSIMs, remaining data).

**Plan cards** — in clients that support [MCP Apps](https://modelcontextprotocol.io/extensions/apps/overview) (Claude, ChatGPT, VS Code and others), `search_esims`, `get_esim` and `compare_esims` results are shown as plan cards (`ui://esimoa/plans.html`). *View plan* opens the plan page on esimoa.com; the cards make no network requests of their own.

## Try asking

- "Find an eSIM for a 7-day trip to Japan."
- "Find a 3-day eSIM for the USA with a local phone number."
- "A 10-day eSIM that works in France, Italy and Spain."
- "A 5-day Japan eSIM on a local network with hotspot, under 20,000 KRW."
- "Compare unlimited data eSIMs for 5 days in Vietnam."
- "Compare the first three plans side by side."

## Partners

esimoa partners can add their API key so the links carry their partner code (commission on purchases through the link): send `X-API-Key: esk_live_…`, or append `?key=esk_live_…` to the URL in clients that cannot set headers. Get a key at the [esimoa Developer Center](https://www.esimoa.com/en/developers).

## This repository

Configuration only — the server runs at `api.esimoa.com`.

- `server.json` — MCP Registry entry
- `.mcp.json` — generic MCP client config (also used by cursor.directory)
- `glama.json` — Glama ownership
- `gemini-extension.json`, `GEMINI.md` — Gemini CLI extension
- `.claude-plugin/marketplace.json`, `plugins/esimoa/` — Claude Code plugin (MCP connection + `find-esim` skill)

Support: support@esimoa.com · [Privacy](https://www.esimoa.com/en/privacy) · [Terms](https://www.esimoa.com/en/terms)

---

## 한국어

AI(Claude·ChatGPT·Gemini·Cursor 등)에서 **이심모아** 여행 eSIM 요금제를 검색·비교하는 MCP 서버입니다. 로그인·키 없이 `https://api.esimoa.com/mcp` 하나만 넣으면 됩니다.

- 여행지·기간·데이터·현지 전화번호·로컬망/로밍·여러 나라 동시·예산·핫스팟·5G 로 거를 수 있어요.
- 마음에 드는 요금제 2~5개를 나란히 비교할 수 있고(`compare_esims`), Claude·ChatGPT 처럼 MCP Apps 를 지원하는 앱에서는 상품 카드로 보여요.
- 요금제마다 이심모아 상품 페이지 링크가 나오고, 결제는 이심모아 사이트에서 해요(AI 안에서 결제하지 않아요).
- 예: "미국 3일, 현지 번호 있는 eSIM 찾아줘", "프랑스·이탈리아·스페인 10일, 세 나라 다 되는 eSIM"
- 연결 방법: [이심모아 개발자 센터](https://www.esimoa.com/ko/developers/docs/mcp)
