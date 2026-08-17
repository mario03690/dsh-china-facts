# dsh-china-facts

China facts your agent can trust: reachability tested from a real mainland backbone, statutory holidays incl. make-up workdays (调休), offline ID/phone validation, lunar calendar.

## What & why

DeepSeek Harness's earliest adopters skew China-side, yet almost every hosted tool assumes a Western network. This plugin serves what only a mainland vantage can: `china_reachability` (real backbone probe + daily-refreshed README badge at `https://ainetcafe.com/badge/china/<host>`), `cn_holiday` with make-up workdays, `id_card_check`, `phone_info`, `lunar_calendar`. All deterministic, keyless, free.

Every set ships `what_can_you_do` — describe a task in any language, get the exact tool + a ready-to-run call.

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
