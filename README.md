# Skycloak — 基于 Cloudflare 全家桶的临时邮箱服务

<p align="center"><a href="README.md">中文</a> | <a href="README_EN.md">English</a> | <a href="CHANGELOG.md">更新日志</a></p>

基于 Cloudflare 免费套餐（Workers / Pages / D1 / KV / Email Routing）构建的临时邮箱服务，功能完整、零成本、无需自有服务器。

- **部署**：`cd worker && pnpm install && cp wrangler.toml.template wrangler.toml`，创建 D1 并执行 [db/schema.sql](db/schema.sql)，配置 `DOMAINS` / `JWT_SECRET` 后 `pnpm run deploy`
- **收件**：在 Cloudflare 控制台将 Email Routing 的 Catch-all 动作设为“发送到 Worker”
- **前端**：`cd frontend && pnpm install && cp .env.example .env.prod`，填入 `VITE_API_BASE` 后 `pnpm build --emptyOutDir && pnpm run deploy`
- **更多**：控制台 / GitHub Actions 等部署方式与完整文档见 [vitepress-docs/](vitepress-docs/)

> 本项目 fork 自 [dreamhunter2333/cloudflare_temp_email](https://github.com/dreamhunter2333/cloudflare_temp_email)（v1.9.0），在原项目基础上整理与维护，版权归上游作者所有并致谢；仅供学习和个人用途。
