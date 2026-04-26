# NBA Data Science Take-Home Assessment

> An R Markdown analysis answering NBA playoff and player-availability questions over team-game and player-game datasets, using the tidyverse for cleaning, EDA, and statistical summaries.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Language](https://img.shields.io/badge/language-R-blue.svg)
![Tools](https://img.shields.io/badge/tools-tidyverse%20%7C%20R%20Markdown-1f6feb.svg)

## Author

**MinJoo Kim**

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Data](#data)
- [Findings](#findings)
- [How to Reproduce](#how-to-reproduce)
- [License](#license)

## Overview

A take-home data-science assessment using NBA team-game and player-game data. The assessment is split into three parts:

| Part | Focus |
|---|---|
| **Part 1** | Data cleaning + descriptive stats (eFG%, win rates, rebound effects) |
| **Part 2** | Player-availability analysis across eligible player-seasons |
| **Part 3** | Written reasoning about season-to-season playoff persistence |

The full analysis (code, narrative, plots) is rendered to `playoffs_project.html`.

## Project Structure

```
.
├── playoffs_project.Rmd    # Source — code, prose, and answers
├── playoffs_project.html   # Rendered report (open in a browser)
├── LICENSE
└── README.md
```

> Note: the input CSVs (`team_game_data.csv`, `player_game_data.csv`) were provided as part of the assessment and are **not included** in this repository.

## Data

The Rmd expects two CSVs in the project root:

| File | Granularity | Used for |
|---|---|---|
| `team_game_data.csv` | one row per team per game | offensive/defensive splits, eFG%, rebound stats |
| `player_game_data.csv` | one row per player per game | minutes played, availability, season aggregates |

After loading, `team_data` is self-joined on `(nbagameid, off_team_name)` and `(nbagameid, def_team_name)` so each row carries both sides of a single game.

## Findings

### Part 1 — Cleaning and descriptive stats

| # | Question | Answer |
|---|---|---|
| 1 | Avg offensive / defensive eFG% | **56.46% / 47.86%** |
| 2 | Higher-eFG team wins | **81.60%** of games |
| 3 | Higher offensive-rebound team wins | **46.21%** of games (i.e. weak signal) |
| 5 | Avg % of games available for eligible player-seasons | **83.3%** |

### Part 2 — Round-by-round win rates for the favored team

| Round | Win rate |
|---|---|
| Round 1 | 60.1% |
| Round 2 | 60.2% |
| Conference Finals | 58.4% |
| Finals | 52.9% |

### Part 3 — Persistence of strong regular-season teams

| Question | Result |
|---|---|
| % of teams with **+5.0 net rating** that make the next-year 2nd round | **63.6%** |
| % of those teams' top-5-minutes players who **played in those 2nd-round series** | **79.0%** |

## How to Reproduce

1. Place the assessment CSVs (`team_game_data.csv`, `player_game_data.csv`) in the project root.
2. Open `playoffs_project.Rmd` in RStudio.
3. Install dependencies:
   ```r
   install.packages(c("tidyverse", "knitr", "rmarkdown"))
   ```
4. Knit to HTML.

## License

MIT — see [LICENSE](LICENSE) for details.
