# SmartWorkingSaving

A lightweight interactive simulator to compare the cost of a day in the office versus a day spent working from home, with monthly totals, annual savings and CO2 impact.

Live demo: https://eagleb.github.io/SmartWorkingSaving/

## Overview

This project helps answer a very practical question: is remote work cheaper than commuting to the office, once you include fuel, tolls, lunch costs, electricity, and seasonal home-heating/cooling costs?

The calculator is intentionally transparent: it shows the monthly delta, annual savings, and the CO2 avoided by working remotely, while also exposing the formulas and assumptions used.

## Current features

- Adjustable parameters for:
  - fuel price or EV charging cost
  - home-to-office distance
  - car consumption / EV consumption
  - tolls
  - remote-work days per week
  - working weeks per year
  - company canteen cost
  - home meal cost
  - PC + monitor power and daily usage hours
  - electricity cost
  - seasonal heating/cooling extras
- ICE/EV vehicle toggle
- Monthly savings chart with positive/negative deltas
- Annual CO2 savings chart with equivalent tree count
- Detailed monthly cost breakdown table
- Collapsible parameter panel
- One-click Excel export (.xlsx) with charts embedded
- Bilingual interface: Italian and English
- Formula and assumption panel at the bottom of the page

## How the model works

The daily comparison is based on this idea:

```text
delta/day = (commuting cost + company canteen cost - home meal cost) - extra home electricity cost
```

The extra home electricity cost includes:
- the PC + monitor energy use during the workday
- a seasonal uplift for heating in winter and fan use in summer
- no full-utility-bill effect, since office utilities are assumed to be paid by the employer

Monthly and annual results are computed from that daily delta multiplied by the configured number of remote-work days and working weeks.

## Assumptions and limitations

- Meal costs are treated as a single-meal cost, not a full-day cost.
- Office lighting, electricity, heating, and cooling are treated as employer-covered costs.
- The model does not include car wear and maintenance, insurance, road tax, commuting time value, or indirect home-office costs.
- Default values are example-based and should be adjusted to reflect your own situation.

## Project structure

- `index.html` — complete app UI, styling, formulas, and logic
- `README.md` — English overview
- `README.it.md` — Italian overview
- `LICENSE` — MIT license

## Running locally

You can open the app directly in a browser:

```bash
start index.html
```

Or serve the project locally:

```bash
python -m http.server
```

Then open http://localhost:8000 in your browser.

## Tech stack

This project is a static single-page app built with:

- HTML + CSS
- React via CDN
- Babel for in-browser JSX compilation
- ExcelJS for spreadsheet export

There is no build step or package installation required.

## License

MIT
