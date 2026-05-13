# Audit Logging — Data Access Policy

## Overview
Every agent query against live data (Supabase, contracts, email, fan records) is logged to `docs/audit-log.jsonl`.

The log records **metadata only** — never raw PII, query results, or contract contents.

## Log Format
Each entry is a single JSON line:

```json
{
  "timestamp": "2026-05-13T09:00:00Z",
  "agent": "data-curator",
  "domain": "data-ip",
  "namespace": "data-ip",
  "query_type": "audience-segment",
  "data_source": "supabase:Fan",
  "user": "iqbal@livescape.asia",
  "session_id": "abc123",
  "result_count": 847,
  "pii_accessed": false
}
```

## Fields

| Field | Description |
|-------|-------------|
| `timestamp` | ISO 8601 UTC |
| `agent` | Which agent ran the query |
| `domain` | Which domain hook triggered it |
| `namespace` | Memory namespace queried |
| `query_type` | Type of query (audience-segment, brand-audit, ip-check) |
| `data_source` | Source system and table (supabase:Fan, file:contract.pdf) |
| `user` | Claude Code session user (from git config email) |
| `session_id` | Session identifier for grouping related queries |
| `result_count` | Number of records accessed (not their content) |
| `pii_accessed` | Boolean — was a PII table touched? |

## Log File
- Path: `docs/audit-log.jsonl`
- Format: newline-delimited JSON (one entry per line)
- Committed to git: yes — provides team-wide audit trail
- Retention: permanent — never truncate or delete entries

## Adding a Log Entry (agents)
When running a data query, append a log entry before returning results:

```
Append to docs/audit-log.jsonl:
{"timestamp": "[ISO timestamp]", "agent": "[your agent name]", "domain": "[domain]", "query_type": "[type]", "data_source": "[source]", "user": "[user email]", "result_count": [n], "pii_accessed": [true/false]}
```
