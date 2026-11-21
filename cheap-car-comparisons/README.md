# Cheap Car Comparisons

A mobile-first public comparison site for UK used electric SUVs, focused on cars advertised **below £21,000** with **at most 50,000 miles**.

**Live GitHub Pages site:** https://mshokry10.github.io/pages/cheap-car-comparisons/

**Source of truth:** A private Google Sheet, `EV SUV Listings Tracker | Under £21k | Nov 2026`, with 23 model tabs and one Overview tab. The raw Google Sheet stays private.

## Site capabilities

- Clear Overview across 23 models showing listing counts, cheapest price, and best-match price independently
- Search and filter across 165 saved candidate adverts
- Dedicated model pages for specifications, evidence, recommended options, uncertainty and individual listing URLs
- Filter by model, price, mileage, manufacturer-approved evidence and listing text
- Display 9 out-of-limit Ford Explorer examples only if **Include excluded watchlist** is enabled
- Side-by-side feature table for up to four chosen adverts, saved locally on the visitor's device
- Read-only exported data with date/staleness disclosure
- Responsive layout for iPhone, Android, tablets and desktop

## Sync

The public `data.json` is a generated, read-only export from the user's private Google Sheet. A scheduled ChatGPT automation re-reads the spreadsheet and regenerates the public file when the **underlying data changes**. It does not publish the private Google document, authentication credentials or personal account information.

Synchronization is **eventual**, not immediate. The page's refresh button fetches the latest **published JSON**, not a direct Google Sheets API result. The UI shows its actual export timestamp. Ads may sell, prices may change, and UK trim options must be verified with the seller.

### Data mapping

Overview: columns A–H, rows 4–27 (name, counts, lowest, selected-best price, notes and research status).

Each model: A–Z with the following ordered fields:
`priority,price,mileage,year,registration,trim,drivetrain,fit,glassRoof,heatedWheel,heatedSeats,camera,driverAssist,heatPump,wltp,boot,history,approved,seller,location,evidence,checks,url,advertId,source,checked`.

Eligibility: numeric price strictly below £21,000; mileage <=50,000; excludes rows beginning `EXCLUDED` and verified Category S/N cases. Excluded examples can appear in their own opt-in watchlist. Parse the **first pound amount**, not all digits from a descriptive price cell (e.g., `£21,989 • £990 over` is £21,989).

The public data can be maintained manually by updating `data.json`; it is never edited by the website.

## Deployment

This folder is inside the existing `mshokry10/pages` repository. GitHub Pages publishes the site's static HTML and JSON from `main`. No build or external server is required.

The original source spreadsheet remains the canonical place to update adverts, prices, notes, links, and best-match values.
