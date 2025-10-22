# Share Volume Analyzer (Citigroup)

A production-ready single-page web application that visualizes common stock shares outstanding for Citigroup (CIK 0000831001) using the SEC EDGAR Open Data API. The app loads a local data.json for initial rendering and supports querying alternate companies via the URL parameter `?CIK=`, updating values live without page reload using a compliant proxy.

## Features
- Live entity display: Title and H1 are driven by data.json and dynamic SEC data
- Max/Min statistics for FY > 2020 with clear, accessible labels
- Responsive, professional UI built with Bootstrap 5
- Trend chart (Chart.js) for filtered series
- Supports alternate companies via `?CIK=0001018724` (or any 10-digit CIK)
- Robust error handling and CORS-friendly proxy fallback
- Static deployment compatible with GitHub Pages

## Setup / Deployment
No build step is required.
- Open `index.html` directly in your browser, or
- Host the repository on GitHub Pages (enabled in this deployment).

The app fetches:
- Local `data.json` to render the initial content
- The SEC endpoint for the default CIK to populate the chart
- A proxied SEC endpoint when you supply `?CIK=` to update the UI dynamically

## Usage Guide
- Open the site. It will display Citigroup stats from `data.json`.
- Optionally append a query parameter to load another company:
  - Example: `index.html?CIK=0001018724` (Amazon.com, Inc.)
- The app will fetch from the SEC API via a CORS-friendly proxy and update:
  - Title and H1 (entity name)
  - Max/Min values and fiscal years
  - Trend chart series

## Technical Overview
- Libraries: Bootstrap 5 (UI), Chart.js (charting)
- Data source: SEC EDGAR Open Data API (Company Concept: `EntityCommonStockSharesOutstanding`)
- Fallbacks: Uses the readable proxy `https://r.jina.ai/http/...` to avoid CORS issues
- Code Structure:
  - `index.html` contains inline CSS and JavaScript for a self-contained SPA
  - Data URIs for attachments are embedded as constants in the JavaScript
  - Functions for computing min/max and rendering the chart
  - Graceful error handling to keep the UI functional

## Files
- `index.html` – Main single-page application
- `data.json` – Precomputed initial data for Citigroup
- `uid.txt` – Attached UID stored exactly as provided (data URI)
- `LICENSE` – MIT License
- `README.md` – Documentation
- `.gitignore` – Standard web project ignores

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
