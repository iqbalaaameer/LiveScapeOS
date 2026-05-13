# Supabase Data Access — Agent Policy

## Overview
Agents in the `data-ip` domain have read-only access to the LiveScape Supabase instance. This is a separate credential from the FanFirst application's write key.

## Access Level
- **Permission:** SELECT only — no INSERT, UPDATE, DELETE, or RPC calls
- **Credential:** Use `SUPABASE_AGENT_READONLY_KEY` environment variable (never commit this key)
- **URL:** Use `SUPABASE_URL` environment variable

## Tables Available to Agents

| Table | Purpose | PII Level |
|-------|---------|-----------|
| `Fan` | Fan profiles | High — anonymize before surfacing |
| `Event` | Event records | Low |
| `Tier` | Ticket tier data | Low |
| `QueueEntry` | Queue positions | Medium — aggregate only |
| `Referral` | Referral data | Medium |
| `DailyShare` | Share tracking | Low |

## Rules
1. Never return raw `email`, `phone`, `stripeCustomerId`, or any identifier fields in agent output
2. Always aggregate to counts, percentages, and averages
3. Minimum segment size before reporting: 10 records (privacy threshold)
4. Every query session triggers an audit log entry (handled by `data-ip` domain hook)

## Connection Example (for agents writing queries)
```
Supabase URL: process.env.SUPABASE_URL
Key: process.env.SUPABASE_AGENT_READONLY_KEY
Client: createClient(url, key, { auth: { persistSession: false } })
```

## Setting Up the Read-Only Key
1. Go to Supabase Dashboard → Settings → API
2. Create a new custom API key with SELECT-only RLS policy
3. Add to your local `.env` as `SUPABASE_AGENT_READONLY_KEY`
4. Never commit `.env` to git
