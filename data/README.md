# Data spec (synthetic only)

**No real invoices, no real people, no real companies.** Everything is invented. This is a spec; the data is generated after Oct 26.

## Mock ledger app
A simple web app that looks like older accounting software: a grid of invoices, an entry form, a Save button, a status toast, and no public API in the demo story. We control its database, so ground truth is exact.

## Invoice fields (synthetic)
`invoice_id` · `vendor_name` (fictional) · `invoice_date` · `amount_inr` · `gst_rate_percent` · `gst_amount_inr` · `total_inr` · `payment_status`

## Dataset size
- 30 runs × 10 invoices = 300 entries
- 10 runs for tuning, 20 held-out (never tune on these)
- Fixed random seed; seed recorded in the repo so the data can be regenerated

## Failure injection
See `failure-catalog.csv`. Each injected failure records: run id, invoice id, failure type, which field, expected value, actual value, and whether the agent's final message still claimed success.

## Variations to make it harder (add if time allows)
Different fonts and zoom levels, a second theme, a cluttered sidebar, slow-loading toast, a modal that covers the grid.

## What not to do
Do not scrape real portals. Do not use real GSTINs, PANs, bank details or names. Do not paste company data from your other projects.
