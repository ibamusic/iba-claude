# iba — plugin for Claude

The IBA connector (`https://mcp.ibamusic.com/mcp`, sign in with your IBA Microsoft account) plus the playbooks for how the team works it. One folder, loaded by claude.ai chat, Claude Desktop (chat and Cowork) and Claude Code.

## What is inside

| Path | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | Manifest, including the remote MCP server (Streamable HTTP, OAuth with Dynamic Client Registration) |
| `skills/iba-connector/` | Starting a session, connecting when the tools are missing, the rules every session follows |
| `skills/iba-finance/` | Invoice and payroll checks, invoice chasing, receipts and statements |
| `skills/iba-amex-monthly/` | The monthly company-card reconciliation |
| `skills/iba-operations/` | Schedules, rosters, availability, booking intake, calendar sync, client reply drafts |
| `skills/iba-schedule-triage/` | Working the schedule-email review queue |
| `skills/iba-executive/` | A company-wide view for leadership, schedule changes only |
| `skills/iba-timesheet/` | Filling the director's biweekly timesheet from every available source |

The skills route to what the server ships — guided prompts, `iba://guide/*` resources and tool descriptions — instead of repeating it. Anything specific (people, mailboxes, vendors, amounts) lives in those server guides, behind the sign-in.
