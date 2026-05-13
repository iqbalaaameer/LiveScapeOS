# LiveScape OS

A Ruflo-powered agent system that automates workflows across all LiveScape business domains — with cross-domain memory sharing and team-synchronized learning via GitHub.

## Domains

| # | Domain | Agents | Status |
|---|--------|--------|--------|
| 1 | Entertainment Operations | venue-analyst, pnl-analyst, contract-reviewer | Active |
| 2 | Artist Research | market-researcher, trend-analyst, artist-evaluator, booking-strategist | Active |
| 3 | Financial Services | invoice-generator, tax-analyst, accounts-auditor | Phase 2 |
| 4 | Product Development | ux-strategist, tech-architect, landing-page-builder | Phase 3 |
| 5 | Data & IP | data-curator, brand-guardian, ip-analyst | Phase 3 |
| 6 | Digital Marketing | content-strategist, campaign-architect, copy-writer | Phase 2 |
| 7 | Agency Services | brand-strategist, creative-director, pitch-writer | Phase 3 |

## Quick Start (Colleagues)

```bash
git clone https://github.com/iqbalaaameer/LiveScapeOS
cd LiveScapeOS
```

Open `.PROMPTS.md` — copy any prompt, fill in the brackets, run it in Claude Code. Agents spawn automatically and query all accumulated team knowledge.

## How It Works

1. **Trigger** — mention a domain keyword (e.g. "P&L", "artist", "invoice")
2. **Agents spawn** — domain-specific team + cross-domain memory loaded
3. **Agents query memory** — see everything the team has learned across all sessions
4. **Output delivered** — P&L, research brief, invoice, campaign plan, etc.
5. **Learnings stored** — patterns committed to git, available to all colleagues

## Memory Architecture

8 namespaces — one per domain plus `livescape-core` for cross-domain signals (e.g. artist research automatically informs P&L estimates).

All memory is git-tracked and synced across the team.

## Folder Structure

```
LiveScapeOS/
├── .claude/
│   ├── settings.json       ← hooks for all 7 domains
│   ├── CLAUDE.md           ← agent definitions and memory map
│   └── projects/*/memory/  ← shared learnings (git-tracked)
├── domains/
│   ├── entertainment/      ← Domain 1: P&Ls, venue, contracts
│   ├── artist-research/    ← Domain 2: talent evaluation, booking
│   ├── financial/          ← Domain 3: invoicing, tax, audit
│   ├── product/            ← Domain 4: web, apps, products
│   ├── data-ip/            ← Domain 5: fan database, brand IP
│   ├── marketing/          ← Domain 6: content, campaigns
│   └── agency/             ← Domain 7: client work, rebrands
├── src/connectors/         ← data access specs (Supabase, audit log)
└── docs/                   ← audit log, documentation
```

## Syncing Learnings

After each session:

```bash
git add .claude/projects/*/memory/
git commit -m "chore: sync [domain] learnings"
git push
```

Colleagues pull → instantly have your accumulated knowledge on their next task.

## Data Access

Agents have read-only Supabase access. Every live data query is logged to `docs/audit-log.jsonl`. Raw PII and contract files are never committed to git. See `src/connectors/` for full policy.
