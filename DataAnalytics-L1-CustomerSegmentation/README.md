# Data Analytics — Level 1, Task 2: Customer Segmentation Analysis

## Objective
Apply clustering algorithms to segment an e-commerce company's customer base into distinct groups based on purchasing behaviour, enabling targeted marketing strategies.

## Dataset
`online_retail.csv` — the classic UCI **Online Retail** dataset: real transactional data from a UK-based online gift retailer (Dec 2010 – 2011), ~65k line items after sourcing, covering InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, and Country.

Source: UCI Machine Learning Repository — Chen, D. (2015). *Online Retail* [Dataset]. DOI: 10.24432/C5BW33.

## Tech Stack
Python, pandas, scikit-learn (KMeans), matplotlib, seaborn, Jupyter Notebook

## What's in this folder
- `Customer_Segmentation.ipynb` — full analysis notebook (executed, all outputs saved)
- `online_retail.csv` — the dataset used
- `charts/` — exported chart PNGs (elbow method, cluster scatter plots, customers per cluster)
- `build_notebook.py` — script used to programmatically generate the notebook

## Analysis Covered
1. Load, inspect, and clean the data (cancellations, missing CustomerIDs, non-positive quantities/prices removed)
2. Descriptive statistics — average order value, purchase frequency, customer lifetime value
3. **RFM feature engineering** — Recency, Frequency, Monetary value per customer
4. Standardisation with `StandardScaler` before clustering
5. **K-Means clustering** with the **Elbow Method** to select K=4
6. Cluster visualisation — scatter plots across Recency×Monetary and Frequency×Monetary
7. Cluster profiling — mean RFM values, customer count, and a plain-language description per cluster
8. Marketing action recommendations tailored to each segment

## Key Findings
Four clusters emerged from the RFM K-Means model:

| Cluster | Profile | Customers |
|---|---|---|
| Champions | Recent, highly frequent, £13k+ avg spend | 14 |
| At-Risk / Lapsed | ~41 days since last order, lowest frequency/spend | 650 |
| Recent, Low-Value | Recent but infrequent, moderate spend | 474 |
| Outlier / Whale | Single customer, one £77k order | 1 |

**Recommendation highlights:**
- Protect the 14 "Champions" with a VIP programme — disproportionately valuable.
- The 650-strong "At-Risk" segment is the biggest win-back opportunity by sheer size.
- The "Whale" customer warrants dedicated account management, not mass marketing.

## How to Run
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook Customer_Segmentation.ipynb
```
