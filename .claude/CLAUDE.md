# Live Scape OS — Ruflo Setup

## Core Agents (Spawned Automatically)

- **finance-analyst**: Reads P&Ls, validates numbers, identifies patterns
- **data-engineer**: Extracts data from multiple concert types, builds models
- **auditor**: Checks for consistency, flags anomalies
- **reviewer**: QA, ensures quality before colleague use

## Memory Sharing

All agents store learnings in namespace `pnl-patterns`:
- Concert type templates (rock, jazz, classical, edm, etc)
- Cost ratios per venue size
- Revenue models by ticket price
- Anomaly patterns

When a colleague works on a new P&L, agents query this namespace automatically.

## Workflow

1. **You work on P&Ls #1-50**
   - Mention "P&L" → hook triggers automatically
   - 4 agents spawn, learn patterns
   - Memory committed to git

2. **Colleague clones repo**
   - Gets your .claude/settings.json (same hooks)
   - Gets your memory (50 concerts worth)
   - Same P&L trigger works for them

3. **Colleague works on P&L #51**
   - Fresh agents spawn (different instance, same config)
   - Agents query shared memory → see all 50 concerts
   - Build faster with accumulated knowledge

## Git Tracking

`.claude/projects/*/memory/` is tracked in git. Commit after each session:

```bash
git add .claude/projects/*/memory/
git commit -m "chore: sync pnl learnings"
git push
```

This ensures colleagues always have the latest knowledge base.

## Expanding

To add more agent types (e.g., marketing-analyst for ticket pricing):
1. Update the hook in settings.json
2. Define agent instructions
3. Commit to git
4. Colleagues pull → automatically get new agents on next P&L task
