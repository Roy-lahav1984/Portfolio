Superstore Sales: Data Analytics Project

Overview

This project analyzes the Sample Superstore dataset to uncover key insights into sales performance, customer behavior, and profitability.  
It demonstrates an end-to-end data analytics pipeline — from cleaning and exploration to customer segmentation using RFM analysis.

---

Dataset

The dataset (commonly used in Tableau and Kaggle projects) contains order-level data for a fictional retail superstore.

| Column | Description |
|---------|--------------|
| `Order ID`, `Order Date`, `Ship Date` | Order identifiers and timeline |
| `Customer ID`, `Customer Name` | Customer details |
| `Segment` | Customer segment (Consumer, Corporate, Home Office) |
| `Region`, `State`, `City` | Geographic details |
| `Category`, `Sub-Category` | Product hierarchy |
| `Sales`, `Quantity`, `Discount`, `Profit` | Financial metrics |

---

Project Structure

```
superstore_analysis/
│
├── superstore_cleaning.ipynb          → Cleans and validates dataset
├── superstore_eda.ipynb               → Performs descriptive and exploratory analysis
├── superstore_rfm_segmentation.ipynb  → Builds RFM-based customer segmentation
├── data/
│   └── SampleSuperstore.csv
└── data_cleaned/
    └── Superstore_Cleaned.csv
```

---

Workflow Summary

1) Data Cleaning (`superstore_cleaning.ipynb`)
Goal: Ensure data integrity and consistency for analysis.

- Removed duplicate entries  
- Handled missing values (mean/mode imputation)  
- Converted date fields to datetime objects  
- Standardized categorical fields (e.g., `Segment`, `Region`)  
- Derived key features:
  - `Ship_Days` → shipping time  
  - `Profit_Margin` = Profit / Sales  

---

2) Exploratory Data Analysis (`superstore_eda.ipynb`)
Goal: Understand sales patterns, customer behavior, and profit drivers.

Key steps
- Summary statistics for Sales, Profit, and Discount  
- Distribution and trend visualizations (Sales vs Profit)  
- Regional and category-level performance analysis  
- Correlation heatmaps for financial metrics  
- Profitability by `Segment` and `Category`

Findings
- Technology category yields highest profit margins  
- Furniture often underperforms due to high discounts  
- Profitability varies strongly by region and shipping mode  
- Some customers consistently purchase high-ticket items with strong margins  

---

3) RFM Segmentation (`superstore_rfm_segmentation.ipynb`)
Goal Classify customers by value and engagement using RFM (Recency, Frequency, Monetary) analysis.

Process
1. Recency Days since the last purchase  
2. Frequency Number of orders placed  
3. Monetary Total spending by each customer  

Steps
- Aggregated customer-level metrics from order data  
- Assigned quantile-based R, F, M scores (1–5)  
- Combined into RFM segments using weighted or concatenated scores  
- Visualized customer clusters by value and retention group

Example Segments
| Segment | Description |
|----------|--------------|
| Champions | Frequent and recent high-value customers |
| Loyal | Repeat buyers with strong lifetime value |
| At Risk | Previously active but inactive recently |
| New Customers | Recent first-time purchasers |
| Lost | Long inactive, low frequency |

Business Impact
- Enables targeted marketing campaigns  
- Supports retention strategies for valuable customers  
- Guides discount and loyalty program optimization

---

Key Insights

1. High-Value Segments  
   The top 20% of customers contribute to more than 60% of total revenue.  

2. Discount Sensitivity  
   Heavy discounts drive sales volume but erode profit — especially in Furniture.  

3. Regional Focus:
   Western and Central regions perform best; Southern regions need margin improvement.  

4. Customer Strategy:  
   Focus retention programs on Loyal and Champions reactivation campaigns for At-Risk customers.

---

Tech Stack

- Python 3.x  
- Pandas / NumPy  
- Matplotlib  
- Scikit-learn (for quantile binning in RFM)  

---

How to Run
Run notebooks in order:  
   - `superstore_cleaning.ipynb`  
   - `superstore_eda.ipynb`  
   - `superstore_rfm_segmentation.ipynb`  


---

Next Steps

- Add Forecasting notebook (ARIMA / Prophet) for monthly sales projections  
- Create an interactive dashboard in Streamlit or Power BI  
- Extend RFM model to include Customer Lifetime Value (CLV)
