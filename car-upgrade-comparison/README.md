# The next car

Mobile-friendly UK SUV comparison, hosted at https://mshokry10.github.io/pages/car-upgrade-comparison/.

## Source and editing

Source spreadsheet: https://docs.google.com/spreadsheets/d/1uHF8Yg4Ihms-_li-x0gGwLMUaspLfz4hcexK8SAH7p8/edit

Edit existing values in the Cars tab. Keep IDs unique and column headers stable. Yes/No in Shortlisted controls the research-shortlist filter; website stars are separate browser-local favourites. New rows are supported if they contain every required field and a unique ID. Changing the sheet does not research or reconfirm adverts automatically.

A ChatGPT automation checks the sheet hourly and commits changed public comparison data. GitHub Pages then rebuilds. The browser fetches data.json on opening, refresh, returning to the tab and every five visible minutes. The export timestamp means when the data last changed/exported, not a new market-price check. Failure to fetch displays an explicit warning and keeps the last available snapshot. Changes flow sheet to page only.

## Public export contract

Only allowlisted headers in data.json fields may be published, selected from Cars A:AH. Never export Cars AI:AN, private insurance quotes, Features B3:B11, sale proceeds, finance details, unrelated tabs or private notes. The Features A21:D27 candidate-screening notes are public research. The sheet itself remains private; its Open spreadsheet link uses normal Google access controls. Calculator inputs are used only in the current browser; favourites and the public comparison cache use localStorage. No analytics, trackers, credentials or server-side financial inputs.

Sync steps:
1. Read the current data.json and current main branch via the connected GitHub app. Read spreadsheet metadata and public Cars values with the connected Google Drive app. Use the actual row count to include added rows; never read/export the private columns as part of a sync.
2. Resolve each existing allowed header by name; reject missing/duplicate headers, duplicate/empty IDs, invalid price/boot/efficiency numbers or unexpected empty source. Require ID, Model and both price allowance numbers. Preserve numeric zero; empty cells remain blank. Pad exported rows to 34 columns. Preserve the fields list exactly.
3. Read only Features A21:D27 for the screened list, with model, verdict, notes and optional URL. No other Features rows belong in the public export.
4. If public rows and screened entries are unchanged, make no commit and no user notification. Otherwise replace data.json with schemaVersion 1, a fresh ISO syncedAt, existing sheetUrl/fields, new rows and screened. Preserve the per-car Research checked dates from the sheet.
5. Read the latest main branch again, create a Git tree based on that commit's tree with only car-upgrade-comparison/data.json changed, create a child commit and update main without force. On concurrent updates, re-read and retry from the new head. Do not overwrite any other file. Verify remote data.json matches the source export and check the Pages workflow result. Report an error only if sync cannot complete; never publish partial or unrelated data.

## Design and calculations

No build step or external JavaScript dependency. Serve this folder using a static server; index.html loads style.css, app.js and data.json.

Budget filter matches the lower shopping allowance. The separate priced-advert filter requires an actual checked price within the ceiling. Advert values are dated research, not live offers; equipment and stock need dealer confirmation. Boot difference uses 504 L Qashqai reference; Tesla is excluded from numeric comparison due to incompatible measurement. Kuga uses seats-back capacity. Kodiaq uses third row folded, and states the all-seats-up limitation.

Energy: annual miles / UK mpg × 4.54609 × petrol £/litre; or annual miles / mi-per-kWh × electricity £/kWh × 1.10. No PHEV estimate without electric-mile share. Inputs are illustrative, not promises of cost or range. No finance, insurance, depreciation or total-ownership-cost claim.
