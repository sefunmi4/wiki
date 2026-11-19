# Relay Financial — Burn-Rate Summary, May–November 2026

Business: Architecture of Homo Sapiens LLC (NJ LLC), holding entity for Architecture of Ashiru and SK Network.

## Export status — November 19, 2026

- Scope: all 14 Relay Financial sub-accounts, May 1 – November 19, 2026, CSV and PDF per sub-account per month
- Status: export in progress in Relay (browser). No statements had been exported yet as of the morning of November 19, 2026. The export was restarted after stalling on the Relay Documents page.
- Once complete, files go to `business/relay-financial/csv/` and `business/relay-financial/pdf/` in this repo, with backups in iCloud Files and Google Drive (see README in this folder).

## Last verified baseline — October 2026

From `strategy/2026-11-08-lessons-learned.md`:

- Total listed operating expenses, October 2026: $53.54
- AWS spending, October 2026: $12.59 (about 23.5% of monthly operating expenses)
- Stale AWS infrastructure identified in November 2026 was eliminated, removing about $12.59/month of AWS expense, or about $151.08/year at the October baseline.
- November month-to-date baseline before cleanup: $3.11, of which about $2.16 was Compute and VPC-related costs.

## How the books are tracked

- Relay Financial, 14 sub-accounts kept separate for operations, expenses, tax, reserve, and label payouts.
- CSV exports are used for gross and net burn-rate calculations, reconciled against the PDF statements before being treated as the authoritative record.
- AI/software tools used for business work (ChatGPT/Codex, Claude, Gemini) are currently paid through personal accounts and should be tracked as business-related fixed operating expenses when appropriate.
- See `ops/aoh-ops-financial-and-label-workflow.md` for the operating workflow.

## Repeat schedule

- Monthly: next run is December 2026
- Then quarterly and yearly repeats, so the accounts are ready for review whenever needed.

This summary contains no account numbers, balances, or transaction details.
