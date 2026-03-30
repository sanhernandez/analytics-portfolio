# 🧩 Customer Segmentation Analysis

> *Identifying high-value customer segments using RFM analysis and K-Means clustering — translating behavioral data into targeted marketing strategies.*

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)

---

## 📈 Project Overview

This project applies **RFM (Recency, Frequency, Monetary) analysis** and **K-Means clustering** to a real-world retail dataset of 541,909 transactions to identify distinct customer segments and generate actionable marketing recommendations.

---

## 🎯 Key Objectives

- **Segmentation** — Group customers into behaviorally distinct clusters
- **RFM Analysis** — Profile customers by recency, frequency, and spending
- **Business Insights** — Translate cluster patterns into targeted marketing strategies

---

## 📂 Dataset

**Source:** Online Retail transactional dataset  
**Size:** 541,909 records → 397,884 after cleaning  

| Column | Description |
|---|---|
| `InvoiceNo` | Transaction identifier |
| `StockCode` | Product code |
| `Description` | Product name |
| `Quantity` | Units purchased |
| `InvoiceDate` | Transaction date & time |
| `UnitPrice` | Price per unit |
| `CustomerID` | Unique customer identifier |
| `Country` | Customer country |

**Sample data:**

| InvoiceNo | Description | Quantity | UnitPrice | Country |
|---|---|---|---|---|
| 536365 | WHITE HANGING HEART T-LIGHT HOLDER | 6 | 2.55 | United Kingdom |
| 536365 | WHITE METAL LANTERN | 6 | 3.39 | United Kingdom |
| 536365 | CREAM CUPID HEARTS COAT HANGER | 8 | 2.75 | United Kingdom |

---

## 🧠 Methodology

### 1. Data Cleaning

```python
import pandas as pd

df = pd.read_csv('online_retail.csv', encoding='ISO-8859-1')

# Remove negative quantities and prices (returns/errors)
df = df[df['Quantity'] > 0]
df = df[df['UnitPrice'] > 0]

# Remove missing CustomerIDs
df = df.dropna(subset=['CustomerID'])
```

**Result:** Reduced from 541,909 → 397,884 valid records  
**Missing CustomerIDs removed:** ~135,080 rows  
**Negative quantities/prices removed:** Likely returns and data errors

---

### 2. Feature Engineering — TotalPrice & RFM Metrics

```python
import datetime as dt

# Create TotalPrice column
df['TotalPrice'] = df['Quantity'] * df['UnitPrice']

# Set snapshot date (day after last transaction)
df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])
snapshot_date = df['InvoiceDate'].max() + dt.timedelta(days=1)

# Compute RFM per customer
rfm = df.groupby('CustomerID').agg({
    'InvoiceDate': lambda x: (snapshot_date - x.max()).days,  # Recency
    'InvoiceNo':   'count',                                    # Frequency
    'TotalPrice':  'sum'                                       # Monetary
})
rfm.columns = ['Recency', 'Frequency', 'Monetary']
```

**RFM metrics defined:**

| Metric | Definition |
|---|---|
| **Recency** | Days since last purchase (lower = better) |
| **Frequency** | Total number of transactions |
| **Monetary** | Total spend across all purchases |

**Sample RFM output:**

| CustomerID | Recency | Frequency | Monetary |
|---|---|---|---|
| 12346.0 | 326 | 1 | 77,183.60 |
| 12347.0 | 2 | 182 | 4,310.00 |
| 12348.0 | 75 | 31 | 1,797.24 |
| 12349.0 | 19 | 73 | 1,757.55 |

---

### 3. Feature Scaling & Elbow Method

```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

# Scale RFM features for clustering
scaler = StandardScaler()
rfm_scaled = scaler.fit_transform(rfm)

# Elbow method to find optimal number of clusters
inertia = []
for k in range(1, 10):
    kmeans = KMeans(n_clusters=k, random_state=42)
    kmeans.fit(rfm_scaled)
    inertia.append(kmeans.inertia_)

plt.plot(range(1, 10), inertia)
plt.title('Elbow Method')
plt.xlabel('Number of Clusters')
plt.ylabel('Inertia')
plt.show()
```

The Elbow Method identified **4 clusters** as the optimal segmentation.

---

### 4. K-Means Clustering

```python
kmeans = KMeans(n_clusters=4, random_state=42)
rfm['Cluster'] = kmeans.fit_predict(rfm_scaled)
```

---

## 📊 Cluster Results

```python
rfm.groupby('Cluster').mean()
```

| Cluster | Recency (days) | Frequency (txns) | Monetary (£) | Profile |
|---|---|---|---|---|
| **0** | 21 | 135 | 2,646 | 🌟 High-Value Actives |
| **1** | 98 | 38 | 774 | 📦 Mid-Tier Regulars |
| **2** | 5 | 2,565 | 126,118 | 💎 VIP / Wholesale |
| **3** | 272 | 25 | 606 | 💤 Lapsed / At-Risk |

### Segment Profiles

**💎 Cluster 2 — VIP / Wholesale** *(smallest group, highest value)*
- Extremely high frequency (avg. 2,565 transactions) and monetary value (avg. £126,118)
- Most recently active (avg. 5 days since last purchase)
- Likely wholesale buyers or top-tier loyal customers

**🌟 Cluster 0 — High-Value Actives**
- Recently active (avg. 21 days), high frequency and spend
- Core segment for retention and upsell strategies

**📦 Cluster 1 — Mid-Tier Regulars**
- Moderate engagement — opportunity to move them into Cluster 0
- Target with re-engagement campaigns

**💤 Cluster 3 — Lapsed / At-Risk**
- High recency (avg. 272 days = ~9 months inactive)
- Low frequency and spend — at risk of churn

---

### Cluster Visualisation

```python
import seaborn as sns

sns.scatterplot(x=rfm['Recency'], y=rfm['Monetary'], hue=rfm['Cluster'])
```

Clusters visualised by Recency vs Monetary value, with Tableau dashboards showing full distribution and behavioral patterns.

---

## 💡 Business Insights

- A **small group of customers (Cluster 2)** generates a disproportionately large share of revenue — a classic Pareto distribution
- **Cluster 0** represents the most actionable high-value segment for loyalty and retention investment
- **Cluster 3** customers (272 days inactive) are at high churn risk and require immediate win-back campaigns
- Customer behavior varies significantly across segments, validating the need for differentiated marketing strategies

---

## 🚀 Business Recommendations

| Segment | Action |
|---|---|
| 💎 Cluster 2 — VIP | Dedicated account management, exclusive offers, early access to new products |
| 🌟 Cluster 0 — High-Value | Loyalty programs, personalised upsell, retention incentives |
| 📦 Cluster 1 — Mid-Tier | Targeted promotions to increase purchase frequency |
| 💤 Cluster 3 — Lapsed | Win-back campaigns, reactivation discounts, churn risk alerts |

---

## 📂 Repository Structure

```
customer-segmentation/
├── customer_segmentation.ipynb   # Full analysis notebook
├── rfm_segments.csv              # RFM output with cluster labels
├── screenshots/                  # Tableau dashboard exports
└── README.md
```

---

## 🛠 Skills Demonstrated

![RFM Analysis](https://img.shields.io/badge/RFM_Analysis-grey?style=flat-square)
![K-Means Clustering](https://img.shields.io/badge/K--Means_Clustering-grey?style=flat-square)
![Feature Scaling](https://img.shields.io/badge/Feature_Scaling_(StandardScaler)-grey?style=flat-square)
![Elbow Method](https://img.shields.io/badge/Elbow_Method-grey?style=flat-square)
![Data Cleaning](https://img.shields.io/badge/Data_Cleaning_(541K_rows)-grey?style=flat-square)
![Tableau](https://img.shields.io/badge/Tableau_Dashboards-grey?style=flat-square)
![Business Analysis](https://img.shields.io/badge/Business_Analysis-grey?style=flat-square)

---

## 🎯 Conclusion

This project demonstrates how clustering techniques applied to transactional retail data can surface meaningful customer segments and directly inform marketing strategy. The combination of RFM feature engineering, StandardScaler normalisation, and K-Means clustering produced four distinct and interpretable segments — each with clear, actionable business implications.

---

> ⚠️ **Note:** The online retail dataset was used as a proxy to demonstrate segmentation methodology. This approach is directly applicable to real-world SME and enterprise marketing analytics scenarios. The original dataset is excluded from the repo due to file size limitations.
