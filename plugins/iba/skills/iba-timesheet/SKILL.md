---
name: iba-timesheet
description: Use to fill the director's biweekly IBA timesheet from every available source — when asked to "fill my timesheet", "do the timesheet", "what did I do the last two weeks", "close out the period", or the morning after a period ends. Reconstructs the two weeks from the sheet, local git, both calendars and IBA database activity, proposes round blocks, and writes them through the connector after a yes. Needs the timesheet grant.
---

# Timesheet fill

The sheet is a record of effort, not a punch clock: round numbers, one plain line per block, about 30–40 hours a week. Pushed commits already appear as development blocks; shows, scheduling, coordination, admin and documentation do not — you add those.

**Read `iba://guide/timesheet` before starting.** It holds the fill rules, the evidence sources in order, the key convention and the report format. This skill is the outline.

## Outline

1. **Ground.** `whoami` — stop if the timesheet grant is missing. `timesheet_periods_list` for the current period and any earlier unsubmitted one; work the oldest first.
2. **Read the sheet.** `timesheet_period_get`. Blocks with a key are yours from an earlier run; blocks without one belong to the ingest or the page — never rewrite them. A day at 6 h or more is covered.
3. **Gather evidence** for each day: local `git log` across the IBA repos (unpushed work), the work calendar and sent mail (Outlook connector), the personal calendar (Google Calendar connector), then IBA activity through this connector — `schedule_search` for rostered shows, `schedule_review_health`, `audit_recent`, `reconciliation_status`. Messaging sources may be added later; they only add evidence, never a new way of writing.
4. **Propose blocks**: one per day per kind of work, 0.5 h steps, categories dev / ops / admin / show / docs / pto / other. Shows at their real times; a weekday with nothing to show is development by default; never pad past target.
5. **Show the table and get a yes**, then one `timesheet_blocks_upsert` per period. Same keys on a re-run update in place; `timesheet_block_delete` removes one of yours.
6. **Report** week totals before → after and what you could not see.
7. **Submit only when asked.** Filling is not submitting. When the owner says to submit an ended period, re-read `timesheet_period_get`, state the total hours, and on their yes call `timesheet_period_submit` with `acknowledged: true`. If the admin site did not answer, re-read `timesheet_periods_list` before any retry.

## Never

- Touch a block without a key, or a submitted period.
- Write before the proposal was approved.
- Submit a period nobody asked you to submit.
- Invent a show or pad a week past target.
