# dsh-china-facts

China facts your agent can trust: reachability tested from a real mainland backbone, statutory holidays incl. make-up workdays (调休), offline ID/phone validation, lunar calendar.

## What & why

DeepSeek Harness's earliest adopters skew China-side, yet almost every hosted tool assumes a Western network. This plugin serves what only a mainland vantage can: `china_reachability` (real backbone probe + daily-refreshed README badge at `https://ainetcafe.com/badge/china/<host>`), `cn_holiday` with make-up workdays, `id_card_check`, `phone_info`, `lunar_calendar`. All deterministic, keyless, free.

Every set ships `what_can_you_do` — describe a task in any language, get the exact tool + a ready-to-run call.

<!-- TOOLS:BEGIN -->
## What's in this pack

10 tools, read from the live endpoint on 2026-08-22 — **this table is generated, not hand-written**, so it cannot drift away from what `tools/list` actually returns. The **Arguments** column is what the tool genuinely reads; it comes from the tool's own declared input schema.

| Tool | What it does | Arguments | Price / call |
|---|---|---|---|
| `what_can_you_do` | Describe a task in plain language (any language) and get back exactly which tools on this server do it, with ready- | `task` | — |
| `china_reachability` | Fetch a URL from a real mainland-China network egress and report HTTP status, latency and China DNS resolution. Ans | `url` | $0.003 |
| `lunar_calendar` | Chinese lunar calendar for any date: 农历、干支纪年、生肖、节气、节日、星座。date omitted = today. | `date` | $0.001 |
| `bazi_chart` | 八字排盘 from birth date and hour: four pillars (年月日时柱), five-element counts, 纳音, zodiac. Uses true solar-term boundari | `datetime` | $0.002 |
| `huangli` | Chinese almanac for a date: 宜 (auspicious activities), 忌 (avoid), 冲煞, 彭祖百忌. date omitted = today. | `date` | $0.001 |
| `pick_lucky_days` | Find auspicious days in a month for an event: 结婚/领证/搬家/开业/装修/出行/签约/订婚/安床/安葬 or any 黄历宜 term. | `month`, `event` | $0.002 |
| `cn_holiday` | Is a date a Chinese public holiday, weekend, or 调休 make-up workday? Plus the next holiday. | `date` | $0.001 |
| `id_card_check` | 中国大陆身份证号校验:check digit validity, birth date, age, gender, region code. id = 18-digit ID number. | `id`, `number` | $0.001 |
| `phone_info` | 中国大陆手机号识别:validity, carrier (移动/联通/电信/虚拟运营商), formatted forms. phone = 11-digit number. | `phone`, `number` | $0.001 |
| `pinyin_convert` | Convert Chinese text to pinyin: with or without tones, first letters only, or as a slug. text = Chinese text. | `text`, `style` | $0.001 |

`—` in the price column means the tool is not metered per call (session/trial-gated instead). Failed calls are never charged. Check it yourself:

```sh
curl -s -X POST https://ainetcafe.com/mcp/cn -H 'content-type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```
<!-- TOOLS:END -->

## Install

```sh
dsh plugin --profile <your-profile> add github:mario03690/dsh-china-facts
```

Thin config layer only (one `@deepseek-ai/dsh-mcp-client` row, shipped as `cordis.patch.yml`) — no tool code runs on your machine. Built against the MCP client config shape of the dsh v0.1 developer preview (2026-08-13); if a later preview changes it, open an issue for a same-day fix.

## Cost, quota, privacy

Free anonymous quota, no signup; every response reports its exact USD cost; failed calls are not charged. Documents are processed in memory and not retained. The config URL carries `?s=dsh-cn` — a channel tag identifying the install path, not you.

**Disclosure:** built and run by the team behind [ainetcafe.com](https://ainetcafe.com) — our own service, free tier plus paid usage. Full bundle (everything at once): [dsh-netcafe](https://github.com/mario03690/dsh-netcafe). MIT.

## Compatibility & permissions (at a glance)

| Signal | This plugin |
| --- | --- |
| **Runtime** | dsh v0.1 developer preview (2026-08-13, Cordis v4). Touches only the MCP client config shape — the narrowest surface available. Verified against a live endpoint on 2026-08-17. |
| **What runs locally** | Nothing. Ships one `cordis.patch.yml` row; there is no tool code, no build step and no lifecycle script in this package. |
| **Filesystem access** | None. |
| **Shell / process access** | None. |
| **Network access** | Outbound HTTPS to `ainetcafe.com` only, from the MCP client that dsh already ships. |
| **Credentials** | None required. No signup, no API key for the free tier. An optional AllRouter key, if you supply one, is sent by dsh as a request header and is never stored by us. |
| **Data retention** | Documents and prompts are processed in memory and not retained. |
| **Dependencies** | One peer dependency: `@deepseek-ai/dsh-mcp-client` (ships with dsh). |
| **License** | MIT (see `LICENSE`). |
| **Publisher** | The team that runs [ainetcafe.com](https://ainetcafe.com) — our own hosted service, free tier plus paid usage. Issues get a same-day reply. |

> A directory listing is not a security review. Read `cordis.patch.yml` — it is short enough to read in full in under a minute.
