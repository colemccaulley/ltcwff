# Python Learning Curriculum — Learn to Code with Fantasy Football

An 8-week curriculum for learning Python using the two repos together:

| Repo | Role |
|------|------|
| [`ltcwff`](https://github.com/colemccaulley/ltcwff) (this repo) | **Your workspace.** Virtual environment, your notebooks, your exercise attempts, milestone projects. Everything you write goes here and gets committed. |
| [`ltcwff-files`](https://github.com/colemccaulley/ltcwff-files) | **The book's materials.** Read-only reference: chapter code to type along with (`code/`), datasets (`data/`), flashcards (`anki/`), and exercise answers (`solutions-to-exercises/`). Don't edit these files — copy from them into this repo when you work. |

The core loop for every chapter:

1. **Read** the chapter in the book.
2. **Type along** with the matching file in `ltcwff-files/code/` — line by line, in a Jupyter notebook or REPL in *this* repo. Never copy-paste; typing is the learning.
3. **Do the end-of-chapter exercises** in a new file here, *before* looking at `ltcwff-files/solutions-to-exercises/`.
4. **Import the chapter's Anki deck** (`ltcwff-files/anki/`) and review flashcards daily (~10 min).
5. **Commit** your work with a message like `Complete ch3.4 granularity exercises`.

> **Setup note:** every book script sets a `DATA_DIR` variable pointing at the author's machine. Change it to wherever your clone of `ltcwff-files/data` lives, e.g. `DATA_DIR = '/Users/colemccaulley/GitHub/ltcwff-files/data'`.

---

## Week 0 — Environment & Tooling (Book Ch. 1)

**Goal:** a working environment and an understanding of the 5-step data analysis framework: *Collect → Store → Load → Manipulate → Analyze*. Each later chapter maps to one of these steps.

- [ ] Clone both repos side by side; create the venv and `pip install -r requirements.txt` (see this repo's README).
- [ ] Launch JupyterLab; learn cells, kernels, restart-and-run-all.
- [ ] Install [Anki](https://apps.ankiweb.net/) and import `anki/00_tooling.apkg` and `anki/01_Intro.apkg`.
- [ ] Skim `ltcwff-files/data/` — open `player_game_2017_sample.csv` and `adp_2017.csv` in a text editor just to see what raw data looks like.

**Deliverable:** a `week0.ipynb` notebook that runs `1 + 1` and prints your Python version. Commit it.

---

## Week 1 — Python Fundamentals (Book Ch. 2)

**Type along:** `code/02_python.py` (293 lines — budget 3–4 sessions)
**Exercises:** end of chapter 2 → check against `solutions-to-exercises/02_python_answers.py`
**Anki:** `anki/02_python.apkg`

Concepts to be able to explain from memory by end of week:

- [ ] Types: strings, ints, floats, booleans
- [ ] Variables and assignment
- [ ] `if` / `elif` / `else`
- [ ] Lists and dicts (and when to use which)
- [ ] `for` loops, then replacing them with **comprehensions**
- [ ] Defining functions; keyword vs positional args
- [ ] `lambda` functions
- [ ] Importing libraries

**Milestone project:** write `scripts/roster_report.py` — pure Python (no pandas): read `data/adp_2017.csv` with the `csv` module, and print the number of players, the top 10 by ADP, and a count of players by position using a dict.

---

## Weeks 2–3 — Pandas, the Heart of the Book (Book Ch. 3)

This is the longest and most important part. Six type-along files, one per section — do roughly three per week:

| Session | File | Topic |
|---------|------|-------|
| 2.1 | `code/03_00_basics.py` | Loading CSVs, DataFrame anatomy, columns/shape/dtypes, indexing, `.loc[]` |
| 2.2 | `code/03_01_columns.py` | Creating & modifying columns: math, string ops, `fillna` |
| 2.3 | `code/03_02_functions.py` | Built-in summaries: `mean`, `sum`, `value_counts`, `crosstab`, `.apply()` |
| 3.1 | `code/03_03_filter.py` | Filtering rows: boolean indexing, `.loc[]`, `.query()`, `isin` |
| 3.2 | `code/03_04_granularity.py` | **`groupby` / `agg` / `stack` / `unstack`** — the hardest topic in the book; do it twice |
| 3.3 | `code/03_05_combine.py` | `merge` and `concat` — uses `data/problems/combine1` (td/touch/yard CSVs) and `combine2` (per-position CSVs) |

**Exercises:** `solutions-to-exercises/03_pandas_answers.py` is 417 lines — the biggest solution file in the book. Do every exercise.
**Anki:** all five `anki/03_0*.apkg` decks, imported as you reach each section.

**Milestone project:** `notebooks/season_summary.ipynb` — start from `data/player_game_2017_sample.csv` (weekly, player-game granularity), group to season level per player, merge in `data/teams.csv`, and produce one tidy table of season totals by player with team info, sorted by fantasy points within position.

---

## Week 4 — SQL (Book Ch. 4)

**Type along:** `code/04_sql.py` — uses Python's built-in `sqlite3` + `pd.read_sql` against `data/fantasy.sqlite`
**Exercises:** `solutions-to-exercises/04_sql_answers.py`
**Anki:** `anki/04_sql.apkg`

- [ ] `SELECT` / `FROM` / `WHERE`
- [ ] Joins across the player, game, and team tables
- [ ] `UNION` and subqueries
- [ ] When to do work in SQL vs pandas (rule of thumb: SQL to get the data out, pandas to shape it)

**Milestone:** one query joining player stats to team data, filtered to a single position, loaded into a DataFrame.

---

## Week 5 — Getting Data: Web Scraping & APIs (Book Ch. 5)

This is the "Collect" step of the framework, and the first week the README's original plan didn't cover.

| Session | File | Topic |
|---------|------|-------|
| 5.1 | `code/05_01_scraping.py` | HTML structure, BeautifulSoup basics |
| 5.2 | `code/05_02_ffc.py` | Real scraper: Fantasy Football Calculator ADP page → DataFrame |
| 5.3 | `code/05_03_api.py` | Public APIs with `requests`: JSON → DataFrame |

**Exercises:** `solutions-to-exercises/05_scraping_answers.py` and `05_api_answers.py`
**Anki:** `anki/05_scraping.apkg`

**Milestone:** modify the FFC scraper to take scoring format and league size as function arguments and return a DataFrame (this is close to exercise 5.1.3 — attempt it before peeking).

---

## Week 6 — Summary Stats & Visualization (Book Ch. 6)

**Type along:** `code/06_summary.py` — seaborn `displot` (distributions) and `relplot` (scatter), faceting by position, Pearson correlation
**Exercises:** `solutions-to-exercises/06_plotting_answers.py`; compare your charts to the reference images `6-1a.png` … `6-2.png`
**Anki:** `anki/06_stats.apkg`

- [ ] Distributions and quantiles (e.g. 95th percentile RB rushing yards)
- [ ] Density plots, faceted by category
- [ ] Scatter plots colored by position
- [ ] Correlation matrices and what they do/don't tell you
- [ ] Titling, labeling, and saving figures

**Milestone:** scatter plot of targets vs fantasy points from `player_game_2017_sample.csv`, colored by position, properly titled and saved to `figures/`.

---

## Week 7 — Modeling (Book Ch. 7)

Requires two libraries not yet in `requirements.txt`:

```bash
pip install statsmodels scikit-learn && pip freeze > requirements.txt
```

| Session | File | Topic |
|---------|------|-------|
| 7.1 | `code/07_01_ols.py` | Linear regression on play-by-play data (`play_data_sample.csv`) |
| 7.2 | `code/07_02_coinflip.py` | Simulation: intuition for randomness and sample size |
| 7.3 | `code/07_03_ols2.py` | Multivariate regression, dummy variables |
| 7.4 | `code/07_04_logit.py` | Logistic regression for binary outcomes (e.g. touchdown probability) |
| 7.5 | `code/07_05_random_forest.py` | Random forests with scikit-learn: train/test split, cross-validation |

**Exercises:** `solutions-to-exercises/07_modeling_answers.py`
**Anki:** `anki/07_modeling.apkg`

**Milestone:** a model predicting whether a play is a run or a pass from down, distance, and field position — report cross-validated accuracy.

---

## Week 8 — Capstone

Combine every step of the framework into one project in `capstone/`, built with clean, reusable functions (the book's Gall's Law: get a simple version working end-to-end first, then extend):

1. **Collect:** scrape current ADP from Fantasy Football Calculator (Week 5 code).
2. **Store/Load:** save to CSV; load it plus the historical samples from `ltcwff-files/data/`.
3. **Manipulate:** merge, filter, and group into an analysis-ready table (Weeks 2–4).
4. **Analyze:** visualize ADP vs actual production by position (Week 6) and fit a simple model of the relationship (Week 7).
5. Refactor the notebook into a script with named functions, and write a short README for it.

---

## Weekly Rhythm

- **4–5 sessions/week, 45–60 min each.** Consistency beats marathons.
- **Every session:** 10 min Anki review first, then type-along or exercises.
- **Every week ends with a commit** of that week's milestone — the git history is your progress log.
- **Stuck ≠ failing.** Struggle for 20–30 minutes before checking a solution; that struggle is where retention comes from. But don't stay stuck past that — read the solution, close it, and re-write it from memory.
- **If a week runs long, let it.** Weeks 2–3 (pandas) commonly take three weeks. `groupby`/`agg`/`unstack` deserves a full extra session on its own.
