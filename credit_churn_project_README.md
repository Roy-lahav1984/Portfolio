
Credit Card Customer Churn Analysis — Data Analytics Project

Overview

This project analyzes customer data from a bank’s credit card portfolio to uncover drivers of churn and retention.  
It focuses on data cleaning, exploratory analysis, and cohort-based retention analytics, without involving machine learning models.  
The aim is to provide actionable business insights that support customer retention strategies.

---

Dataset

Source: Bank Churners Dataset (Kaggle)  
Each row represents a bank customer and their profile, including demographics, account features, and product engagement.

| Feature | Description |
|----------|-------------|
| `Customer_Age`, `Gender`, `Education_Level`, `Income_Category` | Demographics |
| `Months_on_book`, `Total_Relationship_Count` | Tenure & engagement |
| `Credit_Limit`, `Avg_Utilization_Ratio` | Financial indicators |
| `Total_Trans_Amt`, `Total_Trans_Ct` | Spending & activity metrics |
| `churn` | Target flag: 1 = attrited, 0 = active |

---

Project Structure

```
credit_card_churn/
│
├── 01_data_cleaning.ipynb       → Data preparation, missing handling, encoding, and feature engineering
├── 02_eda.ipynb                 → Exploratory analysis of churn patterns and correlations
├── 04_retention_analysis.ipynb  → Cohort & retention analysis over customer tenure
├── data/
│   └── BankChurners.csv
└── data_cleaned/
    └── churn_cleaned.csv
```

---

Workflow Summary

1) Data Cleaning (`01_data_cleaning.ipynb`)

Goal: Prepare dataset for analysis by removing noise and standardizing formats.

Key Steps:
- Removed redundant and identifier columns (`CLIENTNUM`, `Naive_Bayes_*`)  
- Created binary `churn` target variable  
- Handled missing values (median/mode imputation)  
- Encoded categorical variables (ordinal + one-hot)  
- Engineered features:  
  - Utilization & tenure buckets  
  - Activity ratios (`avg_trans_amt`, `ct_change_x_trans`)  

Output: `data_cleaned/churn_cleaned.csv`

---

2) Exploratory Data Analysis (`02_eda.ipynb`)

Goal: Identify key churn drivers and behavioral patterns.

Highlights:
- Class imbalance: ~16% of customers churned  
- Demographics: Slightly higher churn among low-income, low-education segments  
- Behavioral insights:
  - Low transaction count and low credit utilization correlate strongly with churn  
  - High inactivity and frequent contact count predict attrition  
- Correlation analysis:** Activity features show strongest retention influence

Visualization Outputs:
- Churn distribution bar chart  
- Feature-level comparisons (financial, behavioral)  
- Correlation heatmap and churn ranking

---

3) Retention & Cohort Analysis (`04_retention_analysis.ipynb`)

Goal: Measure retention and churn across customer tenure cohorts.

Steps:
- Grouped customers by `Months_on_book` into cohorts (`<12`, `12–24`, …, `72+`)  
- Calculated retention rate per cohort  
- Visualized churn trends over tenure  
- Analyzed engagement metrics (transactions, relationship count) by cohort  
- Built retention “heatmap” comparing churn vs active share

Findings:
- Retention declines steadily with tenure — disengagement grows over time  
- Customers with more relationships and higher activity retain significantly better  
- Long-tenure customers (60+ months) show the highest churn rate — suggesting re‑engagement opportunities  

Business Recommendations:
- Introduce renewal incentives around 36–48 months  
- Offer loyalty rewards or account upgrades to maintain older cohorts  
- Track retention monthly to assess campaign performance  

---

Key Insights

| Theme | Insight |
|-------|----------|
| Engagement | Transaction frequency and relationship depth are top retention drivers |
| Tenure Effect | Churn rises after ~3 years of account activity |
| Customer Profile | Low-income & low-education customers show higher churn |
| Strategic Focus | Prioritize mid-tenure customers (36–60 months) for retention programs |

---

Tech Stack

- Python 3.x  
- Pandas / NumPy / Matplotlib  
- Jupyter Notebook

---

How to Run

Run notebooks sequentially:  
   - `credit_churn_data_cleaning.ipynb`  
   - `credit_churn_eda.ipynb`  
   - `credit_churn_retention.ipynb`  
---
