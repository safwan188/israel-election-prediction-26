# Forecasting Israel's 2026 Knesset election

A seat forecast for the election of 27 October 2026, built in one notebook from public data: the official
results of the seven elections from 2013 to 2022, Central Bureau of Statistics (CBS) locality data and the polls
of the 2026 campaign. The method is tested on the 2021 and 2022 elections before it is applied to 2026.

## Results

From the polls of 15–21 October 2026 and 20,000 simulated elections:

| | Seats, median (80% interval) | Chance of 61 or more |
|---|---|---|
| Netanyahu bloc | 54 (50–59) | 4.5% |
| Opposition | 52 (48–57) | 1.4% |
| Arab lists | 14 (9–17) | – |
| Opposition and Arab lists together | 66 (61–70) | 92% |

Back-test: run from the final week of the 2021 and 2022 campaigns, 21 of 24 lists landed inside their 80% intervals,
and the Netanyahu bloc's result fell inside its interval both times.

## How it works

1. **Data.** Load and clean the CEC results by locality and ballot box (2013–2022), with checks against the official
   totals; join the CBS locality data; give every ballot box a sector (Arab or Jewish).
2. **Exploration.** Turnout by group, the party families over time, the threshold, how stable each party's map is,
   and the vote by socio-economic level.
3. **The seat rule.** Bader-Ofer with surplus agreements, reproducing every official seat of 2013–2022, plus a
   vectorised version about 250 times faster for the simulation.
4. **The polls.** How the final polls of 2021 and 2022 missed, the one correction the misses justify (the Haredi
   parties), the choice of poll average, and the size of the poll error.
5. **Electorate and turnout.** A roll forecast chosen on back-tests and checked against the published 2026 roll, and
   a two-sector turnout model that reproduces every past election.
6. **The model.** The poll average, the Haredi correction, poll errors drawn 20,000 times, seats counted in every draw.
7. **Back-test, forecast, sensitivity, limitations**, and a section that scores the forecast once the results are
   published.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook forecast_2026.ipynb
```

Run the cells from top to bottom (about a minute). Every path is relative to this folder, and the simulations are
seeded, so every run gives the same numbers.

## Contents

| Path | What it is |
|---|---|
| `forecast_2026.ipynb` | the notebook |
| `data/` | the source files; `data/README.md` says where each comes from |
| `outputs/` | the 2026 forecast as CSV, per list and per bloc, written by the notebook |
| `requirements.txt` | the Python packages |
