# RFM Customer Segmentation (Python + Power BI)

End-to-end customer segmentation project using the RFM framework (Recency, Frequency, Monetary) — from raw transactions to an interactive Power BI dashboard.

## Business Goal
Segmenting customers into behavioral segments using RFM to identify the highest-value customers and those at risk of churn, with the aim of improving campaign targeting, increasing revenue from existing customers, and reducing customer attrition.

## Tech Stack
- Python (Pandas, NumPy)
- Power BI (Power Query, Data Model, DAX)

## Dataset
Online Retail II (UCI) transactional dataset.

## Pipeline Overview
### 1) Data Cleaning (Python)
- Removed duplicates and invalid/missing Customer IDs
- Removed cancellations (Invoice starts with "C")
- Filtered sales-only transactions (Quantity > 0, Price > 0)
- Handled outliers using quantile capping
- Created `TotalPrice = Quantity * Price`

### 2) RFM Model
- Snapshot date = (max invoice date + 1 day)
- **Recency**: days since last purchase  
- **Frequency**: number of unique invoices  
- **Monetary**: total spending (`TotalPrice`)  
- Scoring: quantile-based scoring (1–5) using `qcut`

### 3) Segmentation
Segments:
- Champions
- Promising
- New
- At risk
- Can't lose
- Lost

## Outputs
- `data/processed/online_retail_clean.csv`
- `data/processed/customer_rfm.csv`
- Power BI dashboard: `powerbi/rfm_dashboard.pbix`
