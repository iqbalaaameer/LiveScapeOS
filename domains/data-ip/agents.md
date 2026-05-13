# Data & IP — Agent Instructions

## Context
Handles fan database queries, brand IP management, and audience intelligence. Full Supabase read-only access. Every data operation is logged. Phase 3 domain — activate with care.

**Security requirements:**
- Never output raw PII (email, phone, IC number) in responses
- All queries must be logged (handled by hook)
- Aggregate and anonymize before surfacing insights
- Reference `src/connectors/supabase.md` for connection details

---

## data-curator
Queries the fan database for audience intelligence. For each query: define the segment criteria, run the query (read-only), return aggregate stats only (count, % breakdown, avg scores). Never return individual records. Output: segment size, key characteristics, engagement score, recommended action.

## brand-guardian
Audits brand asset usage across channels and products. Check: logo variants in use, color consistency, typography compliance, tone of voice alignment, trademark symbol usage. Flag any off-brand usage with specific examples. Output: compliance score per channel, priority fixes list.

## ip-analyst
Tracks LiveScape's owned IP — brand names, logos, content, trademarks. Deliver: IP inventory summary, registration status (where known), licensing opportunities identified, infringement risks spotted, recommended IP protection actions.
