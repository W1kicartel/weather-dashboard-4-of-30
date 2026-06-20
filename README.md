# 🌤️ Weather Dashboard — Tool 4 of 30

A clean, dependency-light weather dashboard that fetches live conditions and a
7-day forecast for any city in the world. Built as the fourth project in a
*30 tools in 30 days* "building in public" series.

> **Live, no API key needed.** Powered by the free
> [Open-Meteo](https://open-meteo.com/) REST API.

## What it does

- 🔍 **City search** — type any place name; it is resolved to coordinates via the
  Open-Meteo geocoding API.
- 📍 **Use my location** — one click uses the browser Geolocation API.
- 🌡️ **Current conditions** — temperature, "feels like", humidity, wind, and a
  weather icon mapped from WMO weather codes.
- 📈 **7-day temperature chart** — high/low trend rendered with **Chart.js**.
- 🗓️ **7-day forecast grid** — daily icon plus high/low.
- 💾 **Recent cities** — your last six searches are saved in `localStorage` and
  shown as quick-access chips; the most recent one is restored on reload.

## Skills demonstrated

| Area | How it shows up |
|------|-----------------|
| External REST APIs | Two chained endpoints (geocoding → forecast) via `fetch` |
| Async control flow | `async/await`, error propagation, loading states |
| Data visualisation | Chart.js line chart with two datasets |
| State persistence | `localStorage` for recent cities |
| Browser APIs | Geolocation |
| Robustness | HTTP-status checks, empty-result handling, user-facing errors |
| Clean code | Single file, commented, small focused functions |

## Tech stack

- Vanilla **HTML / CSS / JavaScript** (no build step)
- [Chart.js 4](https://www.chartjs.org/) via CDN
- [Open-Meteo](https://open-meteo.com/) geocoding + forecast APIs

## Run it

No installation or keys required — it is a single static file.

```bash
# clone, then just open the file
open index.html        # macOS
# or: start index.html # Windows
# or double-click index.html
```

For the **Geolocation** button to work, browsers require a secure context, so
serve it over `http://localhost` if needed:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## How it works

1. The search box value is sent to the geocoding endpoint, which returns the
   best-matching place with latitude/longitude.
2. Those coordinates are passed to the forecast endpoint, requesting current
   values plus 7 daily records.
3. The response is rendered into three views: the current card, the Chart.js
   trend, and the daily grid.
4. Each successful lookup is stored in `localStorage` so it can be reopened
   instantly later.

## Project structure

```
day-04-weather-dashboard/
├── index.html   # the entire app (markup, styles, logic)
└── README.md
```

---

Part of the **30 tools in 30 days** series by
[@w1kicartel](https://github.com/w1kicartel).
