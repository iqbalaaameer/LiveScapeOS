# Live Scape OS

A Ruflo-powered P&L system where agents learn collaboratively across the entire team.

## Quick Start (Colleagues)

```bash
git clone <repo-url>
cd LiveScapeOS
```

Then just ask:
> "I need a P&L for a classical concert"

The system automatically:
- Detects "P&L" in your request
- Spawns 4 specialized agents
- Loads all previous concert learnings
- Creates your P&L

## Folder Structure

```
LiveScapeOS/
├─ .claude/
│  ├─ settings.json       ← Ruflo config (shared by all)
│  ├─ CLAUDE.md          ← Project rules & agent descriptions
│  └─ projects/*/memory/ ← Shared learnings (git-tracked)
├─ pnl/                  ← P&L examples & templates
│  └─ templates/
├─ agents/               ← Agent instructions & specs
├─ src/                  ← Code (if needed)
└─ docs/                 ← Documentation
```

## How Agents Learn Together

1. **You work on 50 P&Ls** → agents learn concert patterns
2. **Memory gets committed** → stored in git
3. **Colleague clones** → gets all 50 concerts of knowledge
4. **Colleague's agents spawn** → query shared memory automatically
5. **Better P&Ls, faster** → because they learn from your work

## For Colleagues: Pushing Your Learnings

After working on a P&L, commit your memory:

```bash
git add .claude/projects/*/memory/
git commit -m "chore: sync pnl learnings"
git push
```

This makes YOUR learnings available to the next team member.

## Expanding Agents

Want to add a marketing-analyst or venue-negotiator agent? 

1. Update `.claude/settings.json` hook
2. Commit
3. Colleagues pull → new agents available on next P&L task

No need to manually spawn agents—it's all automatic.
