# IPL Cricket Data Analysis & Performance Insights

Exploratory data analysis of IPL match and ball-by-ball data (2008–2022), covering player performance, batting, bowling, partnerships, and team trends.

## Overview

This project analyzes IPL match and ball-by-ball data to uncover insights into player and team performance. It uses `pandas`, `numpy`, `matplotlib`, and `seaborn` to transform raw delivery-level data into season-wise, career-wise, and match-up-level statistics, with a chart accompanying every analytical section.

## Project Structure

```
IPL_Cricket_Data_Analysis_&_Performance_Insights/
├── data/
│   ├── IPL_Ball_by_Ball_2008_2022.csv
│   ├── IPL_Matches_2008_2022.csv
│   └── ipl_deliveries.csv
├── notebooks/
│   └── IPL_Cricket_Data_Analysis_&_Performance_Insights.ipynb
└── README.md
```

## Data

The notebook expects three CSV files, kept in the `data/` folder:

| File | Description |
|---|---|
| `IPL_Ball_by_Ball_2008_2022.csv` | Ball-by-ball delivery data |
| `IPL_Matches_2008_2022.csv` | Match-level metadata (season, teams, result, Player of the Match) |
| `ipl_deliveries.csv` | Delivery data merged with match info to build the core working dataframe |

The notebook's **Setup & Data Loading** section currently loads these from `/content/` (a Colab path). If you're running locally from this folder structure, update those three `pd.read_csv(...)` calls to point at `../data/<filename>.csv` instead.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

## Objectives

- Analyze IPL batting and bowling performance.
- Identify top-performing players across seasons and careers.
- Determine the Purple Cap holder for each season.
- Analyze bowling performance during death overs.
- Study batting performance while chasing a target.
- Examine bowler–batsman dismissal match-ups.
- Reconstruct and analyze batting partnerships from ball-by-ball data.
- Explore season-wise and team-wise IPL trends.

## Sections

1. **Purple Cap Holder for Each Season** — top wicket-taker per season, with economy rate as tie-breaker.
2. **Best Bowler in Death Overs (Overs 16–20)** — top death-over bowler per season.
3. **Season-wise Batting Record for a Player** — a reusable function returning any batter's innings, runs, average, highest score, and strike rate by season.
4. **Player-of-the-Match Performance Summary** — batting and bowling figures for each match's Player of the Match award winner.
5. **Season & Team-wise Trends** — run-scoring trends across seasons (raw and normalized per match) and total wins by team.
6. **Batting While Chasing** — batting performance specifically in the second innings of a match, with a minimum-balls-faced qualifier to keep small-sample players from skewing the rankings.
7. **Batsman Performance Analysis** — a career-wide leaderboard across every batter in the dataset (runs, average, strike rate, highest score, boundaries), distinct from the single-player lookup in Section 3.
8. **Bowler vs Batsman Dismissal Analysis** — the most frequent bowler–batsman dismissal combinations, correctly excluding run-outs and other non-bowler dismissals.
9. **Batting Partnership Analysis** — partnerships reconstructed from ball-by-ball data by tracking the pair of batters at the crease, correctly handling match and innings boundaries; includes the highest individual stands, the most prolific pairs, and team-wise partnership patterns.

## Key Insights

- No single bowler dominates every Purple Cap era — DJ Bravo, B Kumar, and K Rabada are the only repeat winners.
- DJ Bravo is the standout death-overs bowler, topping that table in three different seasons.
- V Kohli leads both all-time IPL runs (6,634) and runs scored while chasing (3,070), though the best chasing/career *averages* and *strike rates* belong to different players depending on role (anchor vs. finisher).
- Even the most-repeated bowler–batsman dismissal pairing in 15 IPL seasons sits at just 7 dismissals — no bowler has a one-sided hold over any single batter in this data.
- AB de Villiers and V Kohli hold both the highest individual partnership (229 off 97 balls, 2016) and the most prolific partnership overall (3,123 runs across 76 stands together).
- 2022 holds the raw run-scoring record, but that's a match-count artifact from the league's expansion to 10 teams — once normalized per match, 2018 was the higher-scoring season.

## How to Run

1. Clone the repo and make sure the three CSV files are in `data/` (see **Project Structure** above).
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open `notebooks/IPL_Cricket_Data_Analysis_&_Performance_Insights.ipynb` in Jupyter (or upload it to Google Colab, along with the `data/` files, and update the paths to `/content/<filename>.csv`).
4. Run all cells top to bottom.

## Notes

- This notebook was cleaned up and restructured from earlier drafts: duplicate/dead cells were removed, sections were consolidated, variable names were made descriptive, and a chart was added to every section.
- Wides are excluded from "balls faced" throughout; byes and leg-byes are excluded from a bowler's runs conceded. Dismissal counts credited to a bowler exclude run-outs, retirements, and obstructing-the-field dismissals.
