# ToolDeals — Milwaukee Deal Tracker

Single-file, offline-friendly web app (`index.html`) for tracking Milwaukee tool deals. Moved over from a Claude chat/Cowork project.

## Tabs

- **Deals** — current deals styled as shelf price tags. Filter by store, search, sort by price or name.
- **Free Offers** — free tool / battery promotions with a live "days left" countdown, plus a short calendar of upcoming sales through Black Friday / Cyber Monday.
- **Watchlist** — tap **Watch price** on any deal or add any Milwaukee tool by hand. Each item has a target price, a price log, and a small history chart with the lowest logged price highlighted. Items at or below target are flagged and sorted to the top.

## Data

Deal, offer and calendar data live in the clearly marked `DEALS` / `OFFERS` / `CALENDAR` block at the top of the `<script>` in `index.html`, with a `SNAPSHOT_DATE`. A static page can't pull live retailer prices, so refresh that block by hand (or ask Claude to). Deals with `price: null` show "Price not captured — check store".

The watchlist is stored in the browser's `localStorage` on each device. Use **Export** / **Import** to back it up or move it between devices.

## Run

Open `index.html` in any browser (works on iPhone — add to Home Screen for an app-like view).
