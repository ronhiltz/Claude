# ToolDeals — Milwaukee Deal Tracker

Single-file, offline-friendly web app (`index.html`) for tracking Milwaukee tool deals. Moved over from a Claude chat/Cowork project.

## Tabs

- **Deals** — current Milwaukee deals across Home Depot, Acme Tools, Amazon, Walmart, Ace Hardware and others, styled as shelf price tags: impact wrenches, ratchets, batteries, chargers (incl. Super Chargers), PACKOUT storage, drills, saws, outdoor and lighting. Filter by store and category, search, sort by biggest % off or price. Deals saving **more than 30%** off retail get a red outline and a SAVE badge; the 🔥 toggle shows only those. Each tag lists its source and date, and expired deals hide automatically.
- **Free Offers** — free tool / battery promotions with a live "days left" countdown, plus a short calendar of upcoming sales through Black Friday / Cyber Monday.
- **Watchlist** — tap **Watch price** on any deal or add any Milwaukee tool by hand. Each item has a target price, a price log, and a small history chart with the lowest logged price highlighted. Items at or below target are flagged and sorted to the top.

## Data

Deal, offer, calendar and watchlist-suggestion data live in the clearly marked `DEALS` / `OFFERS` / `CALENDAR` / `CATALOG` block at the top of the `<script>` in `index.html`, with a `SNAPSHOT_DATE`. A static page can't pull live retailer prices, so refresh that block by hand (or ask Claude to). Each deal records `was` (retail price) or the source's reported `pct` off; the highlight threshold is `HOT_PCT` (30). Deals with `price: null` show "Price not captured — check store".

The watchlist is stored in the browser's `localStorage` on each device. Use **Export** / **Import** to back it up or move it between devices.

## Run

Open `index.html` in any browser (works on iPhone — add to Home Screen for an app-like view).
