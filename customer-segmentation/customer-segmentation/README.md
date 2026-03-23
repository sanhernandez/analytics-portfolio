# Customer Segmentation Analysis

This project demonstrates customer segmentation techniques using Python and Tableau Public, applied to a retail dataset.

It uses clustering to identify high-value customer segments and visualize their behavior, which can guide marketing strategies.

---

## Dataset

- Retail dataset containing transactional information:
  - InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country
- RFM metrics computed:
  - Recency – days since last purchase
  - Frequency – number of transactions
  - Monetary – total spending

---

## Methods

- Exploratory Data Analysis (EDA) – detect outliers and missing data
- Data Cleaning & Feature Engineering – calculated RFM metrics
- Clustering – K-Means applied to segment customers into 4 clusters
- Visualization – Tableau Public dashboards to display clusters and customer metrics

---

## High-Value Segment

- Low Recency + High Frequency + High Monetary = High-Value Customers
- Marketing strategies:
  - Loyalty programs
  - Personalized offers
  - VIP communications

---

## Files

- customer_segmentation.ipynb – Python notebook with clustering
- rfm_segments.csv – dataset with RFM metrics
- screenshots/ – images of Tableau Public dashboards

---

## Notes

- Retail dataset was used as a proxy to demonstrate clustering techniques.
- Methodology can also be applied to SME segmentation.
- The original dataset was excluded due to file size limitations.
