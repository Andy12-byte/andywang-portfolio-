# Reporting Runbook (Sample)

## Purpose
Repeatable steps to refresh a monthly report/dashboard and publish a short status update.

## Owners
- Primary: (name / role)
- Backup: (name / role)

## Inputs
- Source dataset(s): (where the data comes from)
- Reporting period: (YYYY-MM)
- Output(s): dashboard link, scorecard file, summary note

## Refresh steps (example)
1. Run the scheduled job / refresh pipeline.
2. Confirm job succeeded (logs + row counts).
3. Update the scorecard tab for the reporting month.
4. Publish dashboard / export PDF if needed.
5. Send the monthly summary (2–5 bullets: what changed, why, next steps).

## Validation checks
- Row counts within expected range vs last month
- No nulls in key fields (date, identifier, measure)
- Totals reconcile to source
- Spot-check 2–3 KPIs in the dashboard vs query results

## Common issues & quick fixes
- Missing period data: confirm upstream extract; re-run for the period
- KPI jump: check mapping changes, filters, or duplicate rows
- Refresh slow: confirm partition filters / incremental refresh

## Change log
- YYYY-MM-DD — change description — owner
