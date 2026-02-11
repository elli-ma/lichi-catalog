# LICHI — Virtualized Product Catalog

Clothing catalog with infinite scroll and DOM virtualization, connected to the real [Lichi](https://lichi.com) API.

## Features

- **Paginated fetching** — products load in batches of 12 via `useSWRInfinite`, not all at once
- **DOM virtualization** — only visible cards exist in the DOM thanks to `react-window` (FixedSizeGrid)
- **Responsive grid** — 1 to 4 columns depending on screen width via `AutoSizer`
- **Infinite scroll** — automatically fetches the next 6 pages when reaching the bottom
- **Real API** — product data with photos, prices, and sizes comes from `api.lichi.com`

## How Lazy Loading Works

1. First 4 pages (48 products) load on mount
2. `FixedSizeGrid` renders only visible cells — the rest are not in the DOM
3. When the user scrolls to the end, `setSize(size + 6)` requests 72 more products
4. Previously loaded data is cached by SWR

## Tech Stack

- **Next.js 13** (App Router)
- **TypeScript**
- **SWR Infinite** — pagination and request caching
- **react-window** — list virtualization
- **react-virtualized-auto-sizer** — responsive container sizing
- **Tailwind CSS**
