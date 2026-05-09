# Production Security Audit — a Claude Code skill

A Claude Code skill that runs a focused, business-readable production audit on any web project before it ships.

Built by [LogicFlow](https://github.com/Taltal190002-mov) for our own client work, then opened up because the same checklist saves anyone an embarrassing incident on launch night.

## What it does

Triggered automatically when you ask Claude Code things like:

- "is this safe to launch?"
- "production review"
- "pre-launch check"
- "תעבור על האתר לפני שאני מעלה"
- "בדיקת אבטחה לפרודקשן"
- "מוכן ללקוח"

It then runs a five-group audit:

| Group | What it catches |
|---|---|
| 🔴 **A — Stop the launch** | Live API keys in code, plaintext passwords, open admin routes, leaked .env in git history, missing tenant filters, raw SQL string-concat |
| 🔁 **B — Replace, don't patch** | Hand-rolled auth, custom payment forms, app-server SMTP, local-disk uploads on serverless |
| 📈 **C — Hurts at scale** | No rate limits, missing connection pooling, N+1 queries, silent failures, no timeouts on third-party calls |
| 🧰 **D — Operational gaps** | No error monitoring, no backups, no audit trail on admin panel, no uptime alerting |
| ⚖ **E — Compliance / legal** | Missing accessibility statement, outdated privacy policy, PCI scope unclear |

Plus an optional **Group F — live site verification** if a deployed URL is provided (HTTPS, security headers, source maps not exposed, admin routes correctly protected).

The output is a single Markdown report sorted by what blocks the launch, then by what needs replacing, then by what to fix soon. Built for a founder to read in under 3 minutes and act on.

## Install

1. Make sure Claude Code is installed and you have a global skills folder at `~/.claude/skills/`
2. Clone this folder into your skills directory:

```bash
cd ~/.claude/skills
git clone https://github.com/Taltal190002-mov/production-security-audit.git
```

3. Restart Claude Code (close and reopen)
4. Type `/production-security-audit` or just ask "is my site ready to launch?"

## What it is not

- Not a penetration test — for high-stakes systems (banking, healthcare) hire a paid pentester
- Not legal review — Privacy Policy / Terms of Service need a lawyer
- Not accessibility certification — IS 5568 conformance needs an accredited auditor
- Not load testing — use k6 / Locust / Gatling

It catches the obvious 80% of pre-launch problems. The remaining 20% needs domain experts.

## License

MIT — use it, fork it, adapt it for your team.

## Built by

[LogicFlow](https://github.com/Taltal190002-mov) — websites, automation, and digital tooling for small businesses.
