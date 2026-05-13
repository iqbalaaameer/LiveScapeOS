# LiveScape OS — Ruflo Agent System

## Domains & Agents

### Domain 1: Entertainment Operations
Covers P&Ls, venue logistics, artist contracts, show operations.

**Agents:** `venue-analyst`, `pnl-analyst`, `contract-reviewer`, `reviewer`
**Memory namespace:** `entertainment-ops`
**Cross-domain namespace:** `livescape-core`

- `venue-analyst`: Evaluates venue costs, capacity, technical specs, production requirements
- `pnl-analyst`: Builds and validates P&L models, applies historical cost ratios, flags anomalies
- `contract-reviewer`: Reviews artist and venue contract terms, identifies risk clauses
- `reviewer`: QA agent — validates outputs before delivery

### Domain 2: Artist Research
Covers market analysis, talent evaluation, competitive intelligence, booking strategy.

**Agents:** `market-researcher`, `trend-analyst`, `artist-evaluator`, `booking-strategist`
**Memory namespace:** `artist-research`
**Cross-domain namespace:** `livescape-core`

- `market-researcher`: Pulls market data, ticket sales history, comparable shows
- `trend-analyst`: Identifies genre trends, audience demographics, streaming momentum
- `artist-evaluator`: Scores artist viability, fanbase size, touring history, live draw
- `booking-strategist`: Recommends fee ranges, deal structures, ideal markets

### Domain 3: Financial Services
Covers invoicing, accounting, tax compliance, cash flow.

**Agents:** `invoice-generator`, `tax-analyst`, `accounts-auditor`, `cash-flow-analyst`
**Memory namespace:** `financial-services`

- `invoice-generator`: Creates professional invoices from deal data
- `tax-analyst`: Applies Malaysian SST/income tax rules, flags compliance issues
- `accounts-auditor`: Reviews expense records, flags inconsistencies
- `cash-flow-analyst`: Models cash timing, identifies float risks

### Domain 4: Product Development
Covers websites, landing pages, web apps for live entertainment.

**Agents:** `ux-strategist`, `tech-architect`, `landing-page-builder`, `product-analyst`
**Memory namespace:** `product-dev`

- `ux-strategist`: Maps user flows, conversion goals, audience expectations
- `tech-architect`: Recommends stack, integration points, hosting approach
- `landing-page-builder`: Writes copy, structure, and specs for landing pages
- `product-analyst`: Evaluates product-market fit, feature prioritization

### Domain 5: Data & IP
Covers fan database, proprietary brands, audience intelligence.

**Agents:** `data-curator`, `brand-guardian`, `ip-analyst`
**Memory namespace:** `data-ip`
**Security:** All queries logged to `docs/audit-log.jsonl`. Read-only Supabase access only.

- `data-curator`: Queries fan database, segments audiences, identifies patterns
- `brand-guardian`: Enforces brand guidelines across all output
- `ip-analyst`: Tracks owned IP, brand registrations, licensing opportunities

### Domain 6: Digital Marketing
Covers content creation, campaign strategy, social media.

**Agents:** `content-strategist`, `campaign-architect`, `copy-writer`, `performance-analyst`
**Memory namespace:** `digital-marketing`
**Cross-domain namespace:** `livescape-core`

- `content-strategist`: Plans content calendars, platform strategy, tone of voice
- `campaign-architect`: Designs campaign structures, targeting, budget allocation
- `copy-writer`: Writes platform-specific copy, captions, email sequences
- `performance-analyst`: Reviews past campaign data, recommends optimizations

### Domain 7: Agency Services
Covers client rebranding, brand strategy, creative direction.

**Agents:** `brand-strategist`, `creative-director`, `client-analyst`, `pitch-writer`
**Memory namespace:** `agency-services`

- `brand-strategist`: Develops brand positioning, identity frameworks
- `creative-director`: Directs visual and verbal creative output
- `client-analyst`: Builds client profiles, competitive landscape, brief summaries
- `pitch-writer`: Writes proposals, case studies, pitch decks

---

## Memory Architecture

| Namespace | Domain | Purpose |
|-----------|--------|---------|
| `entertainment-ops` | Domain 1 | Concert cost ratios, venue templates, contract patterns |
| `artist-research` | Domain 2 | Booking rates, market trends, artist performance data |
| `financial-services` | Domain 3 | Invoice templates, tax rates, audit flags |
| `product-dev` | Domain 4 | Tech stack decisions, conversion patterns |
| `data-ip` | Domain 5 | Audience segments, brand guidelines |
| `digital-marketing` | Domain 6 | Campaign performance, content patterns |
| `agency-services` | Domain 7 | Client profiles, rebrand outcomes |
| `livescape-core` | Cross-domain | Artist→P&L links, pricing→marketing signals |

Agents always query their domain namespace + `livescape-core` before starting work.

---

## Git Sync (All Domains)

Commit after each work session:

```bash
git add .claude/projects/*/memory/
git commit -m "chore: sync [domain] learnings"
git push
```

Colleagues pull → automatically get all accumulated knowledge.

---

## Rollout Phases

| Phase | Domains Active |
|-------|---------------|
| Phase 1 (now) | Entertainment Ops, Artist Research |
| Phase 2 | Financial Services, Digital Marketing |
| Phase 3 | Agency, Product, Data & IP |
| Fork Ruflo | After 50+ cross-domain patterns in `livescape-core` |

---

## Data Access Policy

- All live data queries use **read-only** Supabase credentials (see `src/connectors/supabase.md`)
- Every data access emits an audit log entry (see `src/connectors/audit-log.md`)
- Raw PII and contract files are **never committed to git** (see `.gitignore`)
- Agents place data files in `domains/*/data/` locally — not synced
