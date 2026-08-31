# Ephemera

Disposable email service built on the Cloudflare free stack — Workers / Pages / D1 / KV / Email Routing. Forked from [dreamhunter2333/cloudflare_temp_email](https://github.com/dreamhunter2333/cloudflare_temp_email) (v1.9.0); upstream copyright stays with the author. For learning and personal use.

> 中文文档见 [README.md](README.md) 的上游原文;[README_EN.md](README_EN.md) 为英文说明。此处为精简版。

## Components

| Path | What it is |
|---|---|
| `worker/` | Cloudflare Worker API: mail receiving (Email Routing catch-all → Worker), address admin, JWT auth |
| `frontend/` | Vue 3 web UI (Pages deploy, `VITE_API_BASE` → worker) |
| `mail-parser-wasm/` | WASM mail parser used by the worker |
| `smtp_proxy_server/` | Python SMTP proxy |
| `vitepress-docs/` | documentation site (full deploy guide incl. console / GitHub Actions deploys) |
| `worker/db/schema.sql` | D1 schema |
| `e2e/` | Playwright end-to-end tests |

## Deploy (short version)

1. `cd worker && npm install && npx wrangler d1 create <db>` — set `DOMAINS` + `JWT_SECRET` in `wrangler.toml`, apply `db/schema.sql`
2. Cloudflare Dashboard → Email Routing → Catch-all → send to Worker
3. `cd frontend` → set `VITE_API_BASE` in `.env.prod` → deploy to Pages (or use the Action in `vitepress-docs`)
4. Full / alternate deploy paths: see `vitepress-docs/`
