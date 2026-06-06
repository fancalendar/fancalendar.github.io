# F1 Schedule

A lightweight, unofficial fan site that shows the current Formula 1 season calendar with session times, a live countdown to the next race, and automatic updates when the schedule changes.

## What it does

- Displays the full F1 calendar for the current season — practice, qualifying, sprint weekends, and race sessions
- Countdown timer to the next race, updating every second
- Automatically fetches the next season's calendar as soon as it is publicly released
- Re-fetches the schedule every 60 seconds to pick up any mid-season changes
- Past races are dimmed, the current race weekend is highlighted
- Circuit track images displayed per race (stored locally in `/tracks/`)

## How it's built

Plain HTML, CSS, and vanilla JavaScript — no frameworks, no build tools, no dependencies. Everything runs client-side in a single `index.html` file.

### API

Data is fetched live from **[Jolpica-F1](https://github.com/jolpica/jolpica-f1)**, the open-source successor to the Ergast Motor Racing API.

- **Base URL:** `https://api.jolpi.ca/ergast/f1/`
- **Endpoint used:** `/{year}.json` — returns the full race calendar for a given season, including dates and times for every session (practice, sprint qualifying, sprint, qualifying, race)
- No API key required
- Free to use

The response is transformed client-side into the format used by the renderer, converting UTC session times to the browser's local timezone.

### Auto-detecting next season

On load, the site fetches the current year's calendar. If no races are returned (the new season hasn't been published yet), it automatically retries with the following year. This means the site will pick up the next season's calendar the moment Jolpica makes it available, with no manual update needed.

## Project structure

```
/
├── index.html       # Everything — markup, styles, and JavaScript
├── README.md
└── tracks/          # Circuit map images (local .png files)
    ├── monaco.png
    ├── silverstone.png
    └── etc...
```

## Running locally

No build step needed. Just open `index.html` in a browser, or serve it with any static file server:

```bash
npx serve .
```

## Disclaimer

This website is unofficial and is not associated in any way with the Formula 1 companies. F1, FORMULA ONE, FORMULA 1, FIA FORMULA ONE WORLD CHAMPIONSHIP, GRAND PRIX and related marks are trade marks of Formula One Licensing B.V.
