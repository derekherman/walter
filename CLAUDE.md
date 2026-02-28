# Walter

An engineering persona for AI agents. Skill + command framework that teaches principal engineering discipline.

## Commands

```bash
npm run dev             # Astro dev server (via @walter/site)
npm run build           # Full chain: sync → optimize → plugin → copy → site → banner
npm run build:plugin    # Plugin build only (via @walter/plugin)
npm run build:site      # Astro site build (via @walter/site)
npm run lint            # Lint all: markdownlint + ESLint + astro check
npm run format          # Prettier
npm run clean           # Remove packages/*/dist/
```

## Docs

- [DEVELOP.md](DEVELOP.md) — Architecture, build system, source format, adding content, development workflow
- [CONTRIBUTING.md](CONTRIBUTING.md) — Setup, making changes, PRs, code style
- [SECURITY.md](SECURITY.md) — Vulnerability reporting
- [README.md](README.md) — User-facing: what Walter is, installation, usage

## Status

- 1 skill, 9 commands, 6 agents, 12 references — all functional, `.walter/` persistence integrated
- Build system: all ESM, deterministic OG/banner output, 4 providers, unified transforms, validation, placeholders, conditionals, auto-copy, ZIPs
- Site: Astro, OG image, SEO meta, sitemap, favicons, 404, analytics (Vercel Analytics + Speed Insights + GA)
- Analytics: event tracking wired on all interactive elements — tabs, copy, download, method pills, theme toggle, outbound links. GA gated on `PUBLIC_GA_ID` env var. Helpers in `packages/site/src/lib/analytics.ts`
- Plugin: marketplace.json + plugin.json ready
- Quality: lint + build pass clean, Husky pre-commit hooks enforced
- CI: GitHub Actions on PR and push to main
- Repo: README, DEVELOP.md, CONTRIBUTING.md, SECURITY.md, issue/PR templates — all in place
- Deployed: walter.cooking live on Vercel, domain pointed, SSL active

## Known Issues

- YAML parser doesn't strip quotes (latent — round-trip works)

## Next

Content audit, frontmatter descriptions, Heisenberg evolution. Set `PUBLIC_GA_ID` in Vercel project settings to activate Google Analytics.

### Remaining Before Release

- **Content audit** — Walk every skill, command, agent, reference for tone, accuracy, completeness
- **Frontmatter descriptions** — Audit all command and agent descriptions for clarity. These are what users and agents see first — clear and accurate, not gimmicky
- **Heisenberg evolution** — Make write-capable, expand agent definition. Walter's subconscious — same thinking and discipline, can do real work (not just read-only advisory). Deep systems thinking + execution
- **Reference optimization** — Reduce token count of reference files loaded at session start. Tighten prose, cut redundancy, preserve all behavior and intent

### Future

**Developer Experience**
- install.sh — Interactive installer (choose provider, target dir, global vs local)

**Extensions**
- Hooks in SKILL.md frontmatter (Claude Code lifecycle events)
- Gemini extension manifest (gemini-extension.json)
- Codex path migration (.codex/prompts/ → .agents/skills/)
- Provider-specific rules

**Bigger Bets & Deferred**
- walter-mcp — Optional MCP server with @modelcontextprotocol/server-memory, queryable graph
- Website download API — On-demand ZIP generation per provider

## Processes

**The loop:** scope → break down → build → verify → hand off. Load Walter (`/walter`), define the problem (`/formula`), decompose it (`/prep`), build with discipline (`/cook`), verify against intent (`/purity`), seal context (`/stash`). Use `/probe` when you need research and `/trace` when something's broken. Every significant piece of work follows this loop — the ceremony scales with the stakes, but the thinking is always the same.

**Making changes:** Edit `packages/`, run `npm run build`, test with the relevant provider, run `npm run lint`. Husky catches lint and format issues at commit time. See [DEVELOP.md](DEVELOP.md) for architecture and source format.

**Keeping docs current:** CLAUDE.md is the bootstrap — status, next action, where to look. Technical detail lives in [DEVELOP.md](DEVELOP.md). Contribution process lives in [CONTRIBUTING.md](CONTRIBUTING.md). Focus on what helps the next agent take their first action.
