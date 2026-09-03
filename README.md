# Lancaster Deals

A searchable, mobile-friendly web app for this week's grocery and store deals across Lancaster County — a project of **Always Lancaster / LancasterOnline**.

**Live site:** deployed on Netlify from the root of this repo.

## What it does
- Search every current circular deal by item or brand; filter by store and department; sort by price, department, store, or ending-soonest.
- **Smart sort** surfaces the best per-unit value first on searches and department filters (e.g. price per ounce for detergent, price per roll for paper towels).
- A per-unit price is shown on each deal wherever a size can be read from the item name.
- Tap **+ Add to list** to build a shopping list, grouped **By Store** or **By Department**, with a running total. Check items off, Copy, or Print. The list is saved on the shopper's own device (localStorage) — no account needed.

## Data
- Source: participating retailers' weekly circulars via the **Flipp / Wishabi** public API, filtered to Lancaster ZIP **17603**.
- `deals.json` — the current week's deals (compact keys; see `build_deals.py`).
- `meta.json` — generation date, store list, department list, and counts.
- This is a point-in-time snapshot; always confirm price, size, and dates in-store. Per-unit prices are estimates and shown only where a size could be read.

## Weekly refresh
`build_deals.py` re-pulls every Lancaster flyer from Flipp, classifies each item into a department, and writes `deals.json` + `meta.json`. A Town routine (**Lancaster Deals Weekly Refresh**) runs it every Wednesday morning and commits the fresh data here; Netlify then auto-deploys. No manual step required.

## Files
| File | Purpose |
|---|---|
| `index.html` | The full single-file app (HTML/CSS/JS, no build step) |
| `deals.json` | Current deals data |
| `meta.json` | Metadata (date, stores, departments) |
| `build_deals.py` | Data generator / weekly refresh script |
