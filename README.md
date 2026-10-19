# IBA Music for Claude

The `iba` plugin connects Claude to IBA Music's operations connector and gives Claude the team's playbooks: payroll and invoice checks, receipt and card-statement reconciliation, schedules and rosters, schedule-email review, and a company-wide view for leadership.

It is for IBA Music staff. The connector only answers people who sign in with an IBA Microsoft account that has an IBA user record, so installing the plugin gives nobody else access to anything.

## Install (one time)

1. In Claude (claude.ai or the desktop app), open **Customize → Plugins → Add → Add marketplace** and enter `ibamusic/iba-claude`.
2. Add the **iba** plugin, then turn on **Sync automatically** for the marketplace so updates arrive by themselves.
3. Open the plugin's **Connectors** tab. If IBA shows **Connected**, you are done. Otherwise select **Add**, then **Connect**, and sign in with your IBA Microsoft account.
4. In a new chat, type **"run whoami"** to see your role and what you can do.

The plugin and the connector belong to your Claude account, so they also work in Cowork, Claude Code and the phone app.

**Claude Code only:** `claude plugin marketplace add ibamusic/iba-claude`, then `claude plugin install iba@iba`, then `/mcp` → IBA → **Authenticate**.

## What is inside

| Skill | For |
|---|---|
| `iba-connector` | Starting a session, connecting, and the rules every session follows |
| `iba-finance` | Invoice and payroll checks, invoice chasing, receipts and statements |
| `iba-amex-monthly` | The monthly company-card reconciliation |
| `iba-operations` | Schedules, rosters, availability, booking intake, client reply drafts |
| `iba-schedule-triage` | Working the schedule-email review queue |
| `iba-executive` | A company-wide view, with schedule changes only |
| `iba-timesheet` | Filling the director's biweekly timesheet from every available source |

What each person can see and change is decided by the connector for their account, not by the plugin.

## Data

The plugin itself holds only instructions. It talks to one service, `https://mcp.ibamusic.com/mcp`, run by IBA Music, which requires an IBA Microsoft sign-in. Nothing in this repository is a credential.

This repository is published automatically; changes made here directly are overwritten.
