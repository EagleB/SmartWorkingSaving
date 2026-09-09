# Office vs. remote work — cost simulator

A small interactive tool to estimate the real cost difference between commuting to the office and working from home, month by month, based on adjustable parameters (fuel price, commute distance, car consumption, toll costs, meal costs, electricity, seasonal heating/cooling).

**[Open the live simulator →](#)** *(replace with your GitHub Pages URL once published)*

## Why

Most "office vs. home" cost comparisons rely on rough guesses. This tool breaks the decision into its actual cost components — commute, meals, and the incremental electricity/heating cost of staying home during the day — so you can see where the numbers actually land for your own situation, and how sensitive the result is to fuel prices or commute distance.

## What it does

- 12 adjustable parameters via sliders: fuel price, commute distance, car fuel consumption, toll cost, remote-work days per month, company canteen cost, home meal cost, PC+monitor power draw, hours powered on, electricity price, and seasonal heating/cooling extra cost.
- Live bar chart showing the monthly delta (positive = remote work saves money, negative = office saves money).
- Detailed monthly table with the underlying cost breakdown.
- A transparency section at the bottom listing every formula and assumption used, so the model isn't a black box.

## How it works

The core logic compares, for a single day:

```
delta/day = (commute fuel cost + canteen cost − home meal cost) − extra home electricity cost
```

Extra home electricity cost = PC/monitor power draw for the day + a seasonal component (full heating in winter, partial in shoulder months, fan cost in summer, zero in mild months). This is only the *incremental* electricity used by staying home during the day — not the full utility bill, since that's paid regardless of where you work.

The monthly and annual totals are the daily delta multiplied by the number of remote-work days set.

Full formulas and assumptions are documented in the page itself, under "Formule e assunzioni."

## Assumptions and limitations

- Canteen and home meal costs are per single meal, not per full day.
- Office electricity/heating/cooling is assumed fully covered by the employer (zero cost to the employee).
- Not included: car wear and maintenance, insurance, road tax, the value of commuting time, or indirect costs of working from home (e.g. home office setup).
- Default values reflect a specific real-world case (short commute, subsidized canteen, moderate heating at 16°C) — adjust the sliders to fit your own numbers.

## Tech

Single self-contained `index.html` file. React and Babel are loaded from CDN (unpkg) — no build step, no dependencies to install. Works as a static page on GitHub Pages or any static host.

## Running locally

Just open `index.html` in a browser, or serve the folder with any static file server:

```bash
python3 -m http.server
```

## Deploying to GitHub Pages

1. Push `index.html` to the root of this repo.
2. Go to **Settings → Pages**.
3. Set **Source** to your default branch, root folder.
4. Your live URL will be `https://<username>.github.io/<repo-name>/`.

## License

Feel free to fork and adapt for your own numbers.
