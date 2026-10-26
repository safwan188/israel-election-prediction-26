# Forecasting Israel's 2026 Knesset election

A seat forecast for the election of 27 October 2026, built in one notebook from public data: the official
results of the seven elections from 2013 to 2022, the final-week polls of those seven campaigns, Central Bureau of
Statistics (CBS) locality data and the polls of the 2026 campaign. The method is back-tested on all seven past
elections, each one with the model's parameters measured on the other six, before it is applied to 2026.

## Results

From the polls of 15–21 October 2026 combined with a flow model of every polling place, 20,000 simulated elections:

| | Seats, median (95% interval) | Chance of 61 or more |
|---|---|---|
| Netanyahu bloc | 55 (46–64) | 11% |
| Opposition | 52 (44–61) | 3% |
| Arab lists | 13 (5–19) | – |
| Opposition and Arab lists together | 65 (56–74) | 84% |

The polls alone give the Netanyahu bloc 54 seats and the flow model alone 59; they are combined 78% to 22% by their
past accuracy. Back-test of the polls model: run from the final week of each of the seven campaigns of 2013–2022,
78 of 80 lists landed inside their 95% intervals, and the Netanyahu bloc's result fell inside its interval all
seven times.

## How it works

The notebook has nine sections:

1. **Introduction.** The question, the results, how Israeli elections work.
2. **The data.** Load and clean the CEC results by locality and ballot box (2013–2022), with checks against the
   official totals; join the CBS locality data; give every ballot box a sector (Arab or Jewish).
3. **What the past tells us.** Turnout by group, the party families over time, the threshold, and how stable each
   party's map is.
4. **The seat rule.** Bader-Ofer with surplus agreements, reproducing every official seat of 2013–2022, plus a
   vectorised version about 250 times faster for the simulation.
5. **The polls.** How the final polls of the seven campaigns of 2013–2022 missed, measured against the vote rather
   than the seats as they fell (seats depend on which lists failed the threshold); the one correction the misses
   justify (the parties to Likud's right are over-polled in every election, and the surplus goes to Likud); the
   choice of poll average; the size of the poll error; and the 2026 poll average.
6. **Population, turnout and the flow model.** A roll forecast chosen on back-tests and checked against the
   published 2026 roll; growth by sector (Haredi 4.5% a year, Arab 3.1%, other Jewish 1.5%); a two-sector turnout
   model that reproduces every past election; and a flow model in which every polling place votes as in its recent
   elections, with its 2026 population.
7. **The model, the back-test and the forecast.** The polls model (poll errors drawn 20,000 times, seats counted in
   every draw), back-tested leave-one-out on the seven elections of 2013–2022; its combination with the flow
   model, weighted by each one's past accuracy; and the 2026 forecast with sensitivity tests.
8. **Limitations, and scoring after the election** once the results are published.
9. **The scenario.** Hand-set turnouts for the Arab sector, the Haredi boxes and other Jewish voters, and the Arab
   lists' loyalty, applied to the 2026 electorate from the growth trends: the Arab and Haredi lists' totals come
   from a three-group turnout model, every other list from the main forecast, rerun with the same errors.

## Read it or run it

The quickest way to read the whole analysis is `forecast_2026.html`: download it and open it in a browser, or
view it rendered at
<https://htmlpreview.github.io/?https://github.com/safwan188/israel-election-prediction-26/blob/main/forecast_2026.html>.

To run the notebook yourself:

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
| `forecast_2026.html` | the executed notebook as one HTML page, to read without running anything |
| `data/` | the source files, all from public sources; `data/README.md` says where each comes from |
| `outputs/` | the 2026 forecast as CSV, per list and per bloc, written by the notebook |
| `requirements.txt` | the Python packages |
