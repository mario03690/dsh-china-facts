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
