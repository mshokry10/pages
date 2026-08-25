# Pages

A small collection of standalone public web pages that I create from time to time and publish with [GitHub Pages](https://pages.github.com/).

This repository is intentionally simple: each page lives in its own directory and can be shared independently with a clean URL. The pages may be comparisons, calculators, reference pages, small tools, or other one-off static websites that do not need their own repository or hosting setup.

## Site structure

Each folder under the repository root represents a separate page or mini-site:

```text
pages/
├── index.html
├── weekly-saas-opportunities/
│   ├── index.html
│   └── data.json
├── mcu-doomsday-watchlist/
│   └── index.html
└── mk5-nursery-comparison/
    └── index.html
```

With GitHub Pages enabled for the `main` branch, the repository is published under:

```text
https://mshokry10.github.io/pages/
```

Individual pages are then available at their directory path, for example:

```text
https://mshokry10.github.io/pages/weekly-saas-opportunities/
```

## Current pages

### Weekly SaaS Opportunities

An interactive, continuously growing archive of research-backed SaaS/startup opportunities. The page reads its content from `data.json`; the weekly opportunity research task regenerates that file after updating the private Google Sheet, so the public dashboard stays current without exposing the spreadsheet or credentials.

**Path:** [`/weekly-saas-opportunities/`](./weekly-saas-opportunities/)

### MCU Road to Doomsday

An interactive post–Far From Home MCU watchlist focused on the useful path toward Spider-Man, Avengers: Doomsday and Avengers: Secret Wars.

**Path:** [`/mcu-doomsday-watchlist/`](./mcu-doomsday-watchlist/)

### MK5 Nursery Comparison

A neutral side-by-side comparison of nursery options around MK5, including fees, funded hours, opening patterns, meals, inspection information, and practical trade-offs.

**Path:** [`/mk5-nursery-comparison/`](./mk5-nursery-comparison/)

## Adding a new page

New pages should normally be self-contained inside a clearly named directory:

```text
my-new-page/
└── index.html
```

Additional CSS, JavaScript, images, or other assets can live alongside that page when needed. Prefer descriptive, location- or topic-specific directory names so URLs remain useful even as more pages are added later.

The root [`index.html`](./index.html) acts as a lightweight directory of the pages that are useful to surface publicly.

## Notes

- Everything in this repository should be treated as **public**.
- Do not commit secrets, API keys, private documents, personal financial information, or anything else that should not be publicly accessible.
- Pages are generally static HTML/CSS/JavaScript and may be updated, replaced, or removed over time.
- Information on individual pages may be specific to the date and context in which that page was created; check the page itself for any relevant caveats or dates.

## Why one repository?

Using one GitHub Pages repository keeps small, shareable pages in one place without creating a new project and deployment setup every time. Each directory still gets its own URL, while the repository remains easy to browse and maintain.
