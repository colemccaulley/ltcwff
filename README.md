# Learn to Code with Fantasy Football

Personal practice repo for working through *Learn to Code with Fantasy Football* by Nathan Braun.

## Environment

- **Python** 3.13, pinned in [`.python-version`](.python-version) — installed automatically by uv
- **Package & environment manager**: [uv](https://docs.astral.sh/uv/) (replaces `venv` + `pip` + `requirements.txt`)
- **Dependencies**: declared in [`pyproject.toml`](pyproject.toml), locked in `uv.lock`
- **Libraries**: pandas, numpy, seaborn, matplotlib, jupyterlab, requests, beautifulsoup4, statsmodels, scikit-learn
- **Editor**: VS Code — workspace settings and recommended extensions live in [`.vscode/`](.vscode)

## Setup

Install uv once (it manages Python itself, so you don't need to install Python separately):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Then clone and sync — one command creates `.venv/`, installs the pinned Python, and installs every locked dependency:

```bash
git clone https://github.com/colemccaulley/ltcwff.git
cd ltcwff
uv sync
```

Open the folder in VS Code (`code .`). It will prompt to install the recommended extensions (Python, Jupyter, Ruff) and automatically use `.venv` as the interpreter. When creating a notebook, pick the `.venv` kernel if asked.

## Daily Workflow

No manual environment activation needed — `uv run` handles it:

```bash
cd ltcwff
code .                        # work in VS Code notebooks/scripts, or:
uv run jupyter lab            # open JupyterLab in browser
uv run python script.py       # run any script inside the environment
```

To add a new package (updates `pyproject.toml` and `uv.lock` together):

```bash
uv add <package>
git add pyproject.toml uv.lock
git commit -m "Add <package>"
```

---

## Learning Plan

> **See [CURRICULUM.md](CURRICULUM.md) for the full 8-week curriculum**, which maps each week to specific files in [ltcwff-files](https://github.com/colemccaulley/ltcwff-files) and adds the web scraping/API and modeling chapters not covered by the outline below.

### Part 0 — Prerequisites and Setup
- [ ] Install and configure VS Code with the Python extension
- [ ] Get familiar with JupyterLab: creating notebooks, running cells, restarting kernel
- [ ] Understand the 5-step data analysis framework: Collect → Store → Load → Manipulate → Analyze
- [ ] Set up Anki and begin using the book's flashcard decks daily

---

### Part 1 — Python Fundamentals
- [ ] Data types: strings, integers, floats, booleans
- [ ] Variables and assignment
- [ ] Control flow: if / elif / else
- [ ] Lists and dictionaries
- [ ] For loops
- [ ] List comprehensions and dict comprehensions
- [ ] Writing and calling functions
- [ ] Lambda (anonymous) functions
- [ ] Importing and using libraries

**Milestone:** Write a Python script that loads a CSV of fantasy stats and prints basic info about it.

---

### Part 2 — Pandas
- [ ] Loading CSVs with `pd.read_csv()`
- [ ] Understanding DataFrame structure: columns, shape, dtypes
- [ ] Indexing: accessing columns, rows, setting/resetting index
- [ ] **The 5 core operations:**
  - [ ] 1. Create and modify columns (math, string ops, `.apply()`, `fillna`)
  - [ ] 2. Built-in summary functions (`mean`, `sum`, `value_counts`, `crosstab`)
  - [ ] 3. Filter rows (boolean indexing, `.loc[]`, `.query()`)
  - [ ] 4. Change granularity (`groupby`, `agg`, `stack`, `unstack`)
  - [ ] 5. Combine DataFrames (`merge`, `concat`)

**Milestone:** Take a player-game dataset and produce a season-level summary table grouped by player and position.

---

### Part 3 — SQL
- [ ] Basic query structure: `SELECT`, `FROM`, `WHERE`
- [ ] Filtering with `WHERE`
- [ ] `JOIN` types: inner, left, right, outer
- [ ] `UNION`
- [ ] Subqueries

**Milestone:** Write a SQL query that joins player stats with team data and filters for a specific season or position.

---

### Part 4 — Visualization
- [ ] Scatter plots with seaborn
- [ ] Density/distribution plots
- [ ] Coloring by category (position, team)
- [ ] Pearson correlation: measuring variable relationships
- [ ] Interpreting and labeling charts clearly

**Milestone:** Produce a scatter plot showing the relationship between target share and fantasy points, colored by position.

---

### Part 5 — Best Practices
- [ ] Apply Gall's Law: start simple, add complexity incrementally
- [ ] Write reusable functions for repeated operations
- [ ] Use clear, descriptive variable names
- [ ] Test code in small pieces before combining
- [ ] Use the REPL/notebook for exploration, scripts for repeatable work

**Milestone:** Refactor a working notebook into clean, well-named functions.

---

## Tips

- **Use the REPL constantly.** Type every example, don't just read it.
- **Don't memorize syntax.** Learn to look things up — tab completion, Google, and StackOverflow are always available.
- **Do exercises before checking answers.** Struggling with a problem is where the learning happens.
- **Focus extra time on Pandas groupby.** `groupby()` + `agg()` + `unstack()` is the hardest concept in the book — revisit it until it feels natural.
- **Commit your notebooks regularly.** Treat each chapter or milestone as a commit so you have a record of your progress.
