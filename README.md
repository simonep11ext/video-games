# 🎮 Best-Selling Video Games Since 2016

A small data analysis project: top games, and sales by platform, genre, publisher, year and region.

## Quick start

```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# 1. Try the pipeline with the included FICTIONAL demo file
python src/analysis.py --csv data/demo_sales.csv --since 2016

# 2. Run it on a real dataset (see "Data" below)
python src/analysis.py --csv data/your_file.csv --since 2016

# 3. Run the tests
pytest -q
```

Results (PNG charts and CSV tables) are written to `outputs/`.

## Data

`data/demo_sales.csv` is **synthetic**: randomly generated titles and sales, only meant to check that the pipeline works. Its results mean nothing.

For real analysis, download a dataset covering 2016 onwards and put it in `data/` (CSV files are git-ignored except `demo_*.csv`):

| Dataset | Covers | Notes |
|---|---|---|
| Kaggle "Video Game Sales" (`vgsales.csv`) | up to 2016 | Too old for a "since 2016" analysis |
| Kaggle "Video Game Sales 2024" (VGChartz) | up to ~2024 | Recommended |

Two formats are detected automatically:

- `Name, Platform, Year, Genre, Publisher, NA_Sales, EU_Sales, JP_Sales, Other_Sales, Global_Sales`
- `title, console, genre, publisher, release_date, total_sales, na_sales, jp_sales, pal_sales, other_sales`

Sales are in millions of units. `pal_sales` is treated as the "EU" region. If your column names differ, edit `COLUMN_MAP` in `src/analysis.py`.

> VGChartz figures are estimates, not official publisher numbers.

## Project structure

```
src/analysis.py      loading, cleaning, analysis, charts
tests/               pytest tests
data/                CSV files (demo file tracked, others ignored)
outputs/             generated charts and tables
```
