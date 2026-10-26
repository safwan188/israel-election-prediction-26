# Data

Every file here is a copy of a public source, unchanged except where noted.

## `cec_results/`: official election results, 2013–2022

The Central Elections Committee (CEC) publishes two files per election: votes per locality
(`results_by_town.csv`) and per ballot box (`results_by_box.csv`). The 2019–2022 files come from
`https://mediaNN.bechirot.gov.il/files/expc.csv` and `expb.csv` (NN = 21 to 25); the 2013 and 2015 files come from
the CEC's legacy site. The CEC publishes them in Windows-1255; these copies are converted to UTF-8.

| Folder | Election | Date |
|---|---|---|
| `k19_2013/` | 19th Knesset | 22 January 2013 |
| `k20_2015/` | 20th Knesset | 17 March 2015 |
| `k21_2019a/` | 21st Knesset | 9 April 2019 |
| `k22_2019b/` | 22nd Knesset | 17 September 2019 |
| `k23_2020/` | 23rd Knesset | 2 March 2020 |
| `k24_2021/` | 24th Knesset | 23 March 2021 |
| `k25_2022/` | 25th Knesset | 1 November 2022 |

`k19_2013/` and `k20_2015/` also hold `official_summary.csv`, the CEC's summary of the lists that won seats
(votes, share, seats).

One edit: the 2013 locality file as published lacks the votes cast outside the voters' home stations, which
the ballot-box file has as 228 boxes under locality code 875. One row with code 875, summed from those boxes, was
added to the locality file.

## `cec_2026/`: the 2026 electoral roll

`registered_voters_2026_by_locality.csv`: registered voters and polling stations per locality for the election of
27 October 2026, summed from the CEC's list of the 12,018 polling stations (`https://www.gov.il/he/pages/26elections-info`).
7,331,981 registered voters in 1,224 localities. The notebook uses it only to check its own forecast of the roll.

## `cbs/`: Central Bureau of Statistics locality data

`bycode2023Sofi.xlsx`: the CBS Localities File 2023 (final). For each locality its Hebrew and English name, district,
locality religion code (1 Jewish, 2 Arab, 3 Bedouin tribe, 4 mixed), municipal status, population and ITM
coordinates. The CBS locality code is the same as the CEC's, so it joins directly to the results.

## `polls/`: published polls

| File | What it is |
|---|---|
| `polls_k24.csv` | 125 published polls of the March 2021 campaign (6 August 2020 to 19 March 2021): date, sample, outlet, pollster and seats per list |
| `polls_k25.csv` | 127 published polls of the November 2022 campaign (6 January to 28 October 2022), same columns |
| `polls_k26.csv` | 120 national polls of the 2026 campaign (29 July to 21 October 2026), extracted from the PDFs every pollster files with the Central Elections Committee (gov.il): seats per list and, for most pollsters, the raw vote share printed beside them |

In the 2021 and 2022 tables some columns change meaning during the campaign (a list renames or merges); the notebook
maps each column to the list it stood for on election day.

## `lists_2026.csv`: the lists of 2026

Compiled for this project. One row per list in the 2026 polls: its key in `polls_k26.csv`, name, family, bloc (as
the pollsters count them), surplus-agreement pair and whether it is on the ballot (Blue and White withdrew on
19 October 2026). The five 2026 surplus agreements, from the Hebrew Wikipedia page of the election (section
"הסכמי עודפים"): A Likud and Religious Zionism, B Yashar! and The Democrats, C Shas and United Torah Judaism,
D Beyahad and Yisrael Beiteinu, E the Joint List and Ra'am.

## `lists_2013_2022.csv`: the main lists of each election

Compiled for this project, not a CEC file. One row per main list of each election: its ballot letters, an
English name, its political family and its official seats (CEC). It covers every list that won seats and a few
that came close. Every other list in the results files counts as "Other". The notebook checks the seats against
the results: the lists with seats must be exactly the lists above the threshold.
