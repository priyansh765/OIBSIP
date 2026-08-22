# Data Analytics — Level 1, Task 3: Cleaning Data

## Objective
Demonstrate professional-level data cleaning skills by taking a deliberately messy dataset and systematically transforming it into a clean, analysis-ready dataset, with every decision documented.

## Dataset
`cafe_sales_dirty.csv` — 10,015 synthetic cafe POS transactions: Transaction ID, Item, Quantity, Price Per Unit, Total Spent, Payment Method, Location, Transaction Date.

Deliberately messy with:
- Missing values across every column (1.4%–33% depending on the column)
- `"ERROR"` / `"UNKNOWN"` placeholder strings mixed into categorical and numeric columns
- Numeric columns (`Quantity`, `Price Per Unit`, `Total Spent`) stored as text because of the placeholder strings
- 15 exact duplicate rows (seeded on top of the source data to demonstrate deduplication)

Source: based on the Kaggle "Cafe Sales — Dirty Data for Cleaning Training" dataset.

## Tech Stack
Python, pandas, numpy, Jupyter Notebook

## What's in this folder
- `Cleaning_Data.ipynb` — full cleaning pipeline notebook (executed, all outputs saved)
- `cafe_sales_dirty.csv` — the raw messy dataset (untouched)
- `cafe_sales_cleaned.csv` — the final cleaned output
- `build_notebook.py` — script used to programmatically generate the notebook

## Cleaning Pipeline
1. **Data quality report** — full inventory of nulls, placeholder anomalies, and dtype issues before any changes
2. **Duplicate removal** — 15 exact duplicate rows identified and dropped (10,015 → 10,000 rows)
3. **Placeholder-to-null conversion** — `"ERROR"`/`"UNKNOWN"` converted to true `NaN` across all columns, since they represent failed data capture, not valid categories
4. **Data type correction** — `Quantity`, `Price Per Unit`, `Total Spent` cast to numeric; `Transaction Date` cast to datetime
5. **Missing data handling, per column, with justification:**
   - `Quantity` / `Price Per Unit` / `Total Spent` — mathematically reconstructed wherever 2 of the 3 related values were known (`Total = Quantity × Price`); remaining gaps filled with the column **median** (robust to skew)
   - `Item` / `Payment Method` / `Location` — filled with an explicit `'Unknown'` label rather than dropped, to avoid discarding otherwise-valid transaction rows
   - `Transaction Date` — rows with an unrecoverable missing date were **dropped** (460 rows), since no date can be safely inferred and time-based analysis can't use a guess
6. **Standardisation** — categorical text normalised to Title Case for consistency
7. **Outlier detection** — IQR method applied to all numeric columns (result: 0 outliers found, confirming internal consistency)
8. **Before vs. after summary table** — row count, duplicate count, null count, and dtypes compared pre/post cleaning
9. **Cleaned dataset saved** to `cafe_sales_cleaned.csv`

## Results
| Metric | Before | After |
|---|---|---|
| Rows | 10,015 | 9,540 |
| Duplicate rows | 15 | 0 |
| Total null cells | thousands (see notebook) | **0** |
| Quantity / Price / Total Spent dtype | text (object) | numeric (float64) |
| Transaction Date dtype | text (object) | datetime64 |

## How to Run
```bash
pip install pandas numpy jupyter
jupyter notebook Cleaning_Data.ipynb
```
