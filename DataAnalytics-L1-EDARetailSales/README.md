# Data Analytics — Level 1, Task 1: EDA on Retail Sales Data

## Objective
Perform a thorough Exploratory Data Analysis on a retail sales dataset to uncover patterns, customer behaviour trends, and actionable business insights.

## Dataset
`retail_sales_dataset.csv` — 1,000 retail transactions with the following columns:

| Column | Description |
|---|---|
| Transaction ID | Unique ID per transaction |
| Date | Date of purchase |
| Customer ID | Unique customer identifier |
| Gender | Customer gender |
| Age | Customer age |
| Product Category | Beauty / Clothing / Electronics |
| Quantity | Units purchased |
| Price per Unit | Price per unit ($) |
| Total Amount | Quantity × Price per Unit ($) |

Source: publicly available "Retail Sales Dataset" (originally from Kaggle).

## Tech Stack
Python, pandas, matplotlib, seaborn, Jupyter Notebook

## What's in this folder
- `EDA_Retail_Sales.ipynb` — the full analysis notebook (executed, with all outputs saved)
- `retail_sales_dataset.csv` — the dataset used
- `charts/` — all exported chart PNGs
- `build_notebook.py` — script used to programmatically generate the notebook

## Analysis Covered
1. Initial data inspection (shape, dtypes, null check)
2. Descriptive statistics (mean, median, mode, std) for all numerical columns
3. Time series analysis — monthly and quarterly sales trend line charts
4. Customer demographics — age group distribution and gender breakdown
5. Product analysis — top-selling categories and revenue by category (bar chart)
6. Correlation heatmap of numerical variables
7. An additional non-obvious visualisation: average order value by day of week
8. Written observations after every chart (markdown cells throughout the notebook)
9. Conclusion section with 4 specific, actionable business recommendations

## Key Insights
- Sales peak in **May and Q2** — the best window for promotional campaigns.
- **Electronics** drives the highest revenue despite comparable transaction counts to Clothing/Beauty, due to a higher price per unit.
- Purchases are roughly gender-balanced (51% Female / 49% Male).
- The **56–64 age group** spends the least — a target for re-engagement offers.
- `Total Amount` correlates strongly with `Price per Unit`, weakly with `Age`.

## How to Run
```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook EDA_Retail_Sales.ipynb
```
Or view the notebook directly on GitHub — all outputs are pre-rendered.
