# Forecasting Israel's 2026 Knesset election

A seat forecast for the election of 27 October 2026, built in one notebook from public data: the official
results of the seven elections from 2013 to 2022, the final-week polls of those seven campaigns, Central Bureau of
Statistics (CBS) locality data and the polls of the 2026 campaign. The method is back-tested on all seven past
elections, each one with the model's parameters measured on the other six, before it is applied to 2026.

## Results

### The main forecast (section 7)

From the polls of 15–21 October 2026 combined with a flow model of every polling place, 20,000 simulated elections:

| | Seats, median (60% interval) | Chance of 61 or more |
|---|---|---|
| Netanyahu bloc | 55 (51–59) | 11% |
| Opposition | 52 (48–56) | 3% |
| Arab lists | 13 (10–16) | – |
| Opposition and Arab lists together | 65 (61–69) | 84% |

Per list, with the expected seats (the mean of the simulated elections) and the median with its 60% interval:

| List | Bloc | Vote % | Expected seats | Median (60% interval) | Chance of passing |
|---|---|---|---|---|---|
| Likud | Netanyahu | 19.4 | 25.0 | 25 (23–27) | 100% |
| Shas | Netanyahu | 6.7 | 8.4 | 8 (7–10) | 99% |
| Otzma Yehudit | Netanyahu | 5.9 | 7.1 | 7 (5–9) | 96% |
| United Torah Judaism | Netanyahu | 5.7 | 7.0 | 7 (5–9) | 94% |
| Religious Zionism and Zehut | Netanyahu | 5.0 | 5.7 | 6 (4–8) | 87% |
| Amkha Yisrael | Netanyahu | 2.7 | 1.9 | 0 (0–5) | 37% |
| Yashar! with Eisenkot | Opposition | 16.7 | 21.6 | 21 (20–23) | 100% |
| Beyahad | Opposition | 9.1 | 11.6 | 12 (10–13) | 100% |
| The Democrats | Opposition | 7.5 | 9.4 | 9 (8–11) | 100% |
| Yisrael Beiteinu | Opposition | 5.8 | 7.1 | 7 (6–9) | 95% |
| Hendel and Zelekha | Opposition | 3.0 | 2.3 | 0 (0–5) | 45% |
| Joint List | Arab lists | 6.5 | 8.1 | 8 (6–10) | 98% |
| Ra'am | Arab lists | 4.4 | 4.8 | 5 (0–7) | 77% |

The polls alone give the Netanyahu bloc 54 seats and the flow model alone 59; they are combined 78% to 22% by their
past accuracy. Back-test of the polls model: run from the final week of each of the seven campaigns of 2013–2022,
60 of 80 lists landed inside their 60% intervals (three in four: the intervals are wide for their label), and the
Netanyahu bloc's result fell inside its interval all seven times.

### The scenario (section 9)

The same simulation with the turnouts set by hand instead of carried from the past: 64–67% in the Arab sector at the
ballot boxes (2022: 52.6%, the 2020 record 63.7%), 75% at the Haredi boxes (2022: 73.5%), 70–72% among other Jewish
voters (2022: 73.4%), 87–88% of the Arab sector's vote to the Arab lists (2022: 85.1%) with the Joint List taking 60%
of it, all on the 2026 electorate from the growth trends. The Arab and Haredi lists' totals come from a three-group
turnout model; every other list keeps its share of what is left, so the polls still decide the centre and Likud.

| | Seats, median (60% interval) | Chance of 61 or more |
|---|---|---|
| Netanyahu bloc | 54 (51–58) | 8% |
| Opposition | 48 (45–52) | 0.2% |
| Arab lists | 17 (15–20) | – |
| Opposition and Arab lists together | 66 (62–69) | 88% |

| List | Bloc | Vote % | Expected seats | Median (60% interval) | Chance of passing |
|---|---|---|---|---|---|
| Likud | Netanyahu | 18.2 | 23.4 | 23 (21–25) | 100% |
| Shas | Netanyahu | 7.7 | 9.7 | 10 (8–11) | 100% |
| United Torah Judaism | Netanyahu | 6.5 | 8.1 | 8 (6–10) | 98% |
| Otzma Yehudit | Netanyahu | 5.6 | 6.5 | 7 (5–8) | 93% |
| Religious Zionism and Zehut | Netanyahu | 4.7 | 5.1 | 6 (4–7) | 82% |
| Amkha Yisrael | Netanyahu | 2.6 | 1.7 | 0 (0–4) | 33% |
| Yashar! with Eisenkot | Opposition | 15.7 | 20.1 | 20 (18–22) | 100% |
| Beyahad | Opposition | 8.5 | 10.8 | 11 (9–13) | 100% |
| The Democrats | Opposition | 7.1 | 8.8 | 9 (7–11) | 99% |
| Yisrael Beiteinu | Opposition | 5.5 | 6.5 | 7 (5–8) | 92% |
| Hendel and Zelekha | Opposition | 2.9 | 2.1 | 0 (0–5) | 40% |
| Joint List | Arab lists | 8.3 | 10.6 | 11 (9–12) | 100% |
| Ra'am | Arab lists | 5.6 | 6.7 | 7 (5–9) | 93% |

The Arab lists gain four seats on the main forecast, three of them from the turnout and one from no Arab votes being
wasted below the threshold; the Haredi lists gain three, mostly from the growth of their electorate.

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
   from a three-group turnout model, every other list from the main forecast, rerun with the same errors; and a
   lever for the 810,000 citizens on the roll who live abroad.

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
