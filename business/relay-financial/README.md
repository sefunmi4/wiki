# Relay Financial — Architecture of Homo Sapiens LLC

Dedicated business folder for Relay Financial statements for Architecture of Homo Sapiens LLC (NJ LLC).

## Structure

- `csv/` — CSV transaction exports, one file per sub-account per month
- `pdf/` — PDF statements, one file per sub-account per month

Note: the GitHub connector cannot push binary files, so PDF statements are stored in Google Drive (Architecture of Homo Sapiens Relay Financial / PDF/) rather than in `pdf/` here. The `pdf/` folder is kept for per-account PDFs added by other means.

## Naming

`relay__<last-4>__<YYYY-MM>.csv` / `.pdf`

Example: `relay__7309__2026-10.csv`

Combined PDFs are named `relay-statements-2026-05-to-2026-08.pdf`, `relay-statements-2026-08-to-2026-11.pdf`, and `relay-statements-2026-11.pdf`.

## Coverage

- All 14 Relay sub-accounts
- Period: May 2026 – November 2026, then monthly, quarterly, and yearly repeats
- December 2026 is the next monthly run
- PDF statements: complete, 98 of 98 (May–November 2026)
- CSV exports: partial — Operating ••••7309 complete May–November 2026; other months/accounts to be filled from the iCloud copies. See `2026-burn-rate-summary.md` for the full gap list.

## Backups

- iCloud Files: iCloud Documents / iPhone Downloads / Architecture of Homo Sapiens / Architecture of Homo Sapiens Relay Financial
- Google Drive: Architecture of Homo Sapiens Relay Financial folder (https://drive.google.com/drive/folders/1pIsJI9eJN05_1XhBEj9w1NqBWaWHzAP4), with CSV/, PDF/, and Google Sheets/ subfolders

## Accounting

Use the CSV exports for gross and net burn-rate calculations, reconciled against the PDF statements. See `ops/aoh-ops-financial-and-label-workflow.md` for the operating workflow.

Note: this repository is public. Review files before adding them here.
