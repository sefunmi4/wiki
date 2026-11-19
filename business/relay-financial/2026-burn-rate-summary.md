# Relay Financial — Burn-Rate Summary, May–November 2026

Business: Architecture of Homo Sapiens LLC (NJ LLC), holding entity for Architecture of Ashiru and SK Network.

## Export status — completed November 19, 2026

- Scope: all 14 Relay Financial sub-accounts, May 1 – November 19, 2026, CSV and PDF per sub-account per month
- Status: export completed November 19, 2026 (browser export, 08:10–08:46 EST, after the Relay magic-link sign-in). Files filed the same day.
- PDF statements: **complete — 98 of 98 monthly statements**, all 14 accounts, May–November 2026. Verified by page count: combined PDF `relay-statements-2026-05-to-2026-08.pdf` (96 pages, 48 statements) + `relay-statements-2026-08-to-2026-11.pdf` (100 pages, 50 statements), plus `relay-statements-2026-11.pdf` (28 pages, November only). November is a partial month (Nov 1–19, 2026).
- CSV exports: **partial**. Operating ••••7309 is complete for all 7 months (48 transactions). Header-only CSVs (no transactions, $0 accounts) for Guild Events ••••6889 (May–Jul), Owner's Pay ••••6874 (Nov), and Sponsor Escrow ••••6895 (Aug). A custom transaction report covering May 1–August 31, 2026 (61 transactions, all 14 accounts) is included. Relay's custom transaction report failed for ranges covering September–November with Relay's own error "Couldn't export the report", and Relay has no combine-into-one option for CSV, so the remaining monthly CSVs were not captured as individual files in this run.
- Where the files live: PDF statements are in Google Drive (Architecture of Homo Sapiens Relay Financial / PDF/), because the GitHub connector cannot push binary files. CSV files are in `business/relay-financial/csv/` in this repo and in Google Drive (CSV/). A Google Sheets workbook ("Relay Financial — May-Nov 2026 — Architecture of Homo Sapiens") is in Google Drive (Google Sheets/) — it is still empty pending the Google Sheets connection; the CSVs are the data source to fill it.
- Missing CSVs: monthly CSVs for the 13 non-Operating sub-accounts (except the header-only ones listed above) are to be filled from the iCloud copies in iCloud Documents / iPhone Downloads / Architecture of Homo Sapiens / Architecture of Homo Sapiens Relay Financial.

## Balances — November 19, 2026

Total across all 14 sub-accounts: **$695.93**

| # | Sub-account | Last 4 | Balance, Nov 19, 2026 |
|---|-------------|--------|-----------------------|
| 01 | Operating Checking | 7309 | $100.00 |
| 02 | Tax Checking | 6865 | $257.50 |
| 03 | Profit Checking | 6872 | $51.50 |
| 04 | Owner's Pay Checking | 6874 | $0.00 |
| 05 | COGS - Pod Shop Checking | 6890 | $0.00 |
| 06 | Operating Expenses Checking | 6888 | $286.93 |
| 07 | Emergency Reserve Savings | 7310 | $0.00 (APY 1.19%) |
| 08 | Guild Events Checking | 6889 | $0.00 |
| 09 | Sponsor Escrow Checking | 6895 | $0.00 |
| 10 | Legal and Compliance Checking | 6899 | $0.00 |
| 11 | Guild Quest Bounty Fund Checking | 6913 | $0.00 |
| 12 | Quest Support and Production Checking | 6918 | $0.00 |
| 13 | COGS - Platform Infrastructure Checking | 6920 | $0.00 |
| 14 | Marketing Acquisition Campaigns Checking | 6925 | $0.00 |

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

This summary lists only last-4 account numbers and the total balance as of November 19, 2026. It contains no full account numbers or transaction details.
