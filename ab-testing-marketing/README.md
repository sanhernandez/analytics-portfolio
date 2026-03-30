# 📊 A/B Testing & Campaign Analytics

> *Evaluating marketing campaign performance using SQL analysis and statistical testing — translating data into budget and strategy decisions.*

![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)

---

## 📈 Project Overview

This project analyses an A/B marketing experiment comparing two campaign variants (A vs B) across key performance indicators — **Conversion Rate, CTR, and Revenue** — using SQL for metric computation and statistical testing to validate findings. Results are visualised through Tableau Public dashboards.

---

## 🎯 Key Objectives

- **A/B Testing** — Compare campaign variants and measure performance differences
- **SQL Analysis** — Calculate marketing KPIs directly in a SQLite database via Jupyter
- **Statistical Validation** — Confirm results with a t-test (p < 0.05)
- **Business Insights** — Translate findings into concrete budget and strategy recommendations

---

## 📂 Dataset

Campaign performance data simulating a real-world A/B marketing experiment:

| Column | Description |
|---|---|
| `user_id` | Unique user identifier |
| `group_name` | Campaign variant (A or B) |
| `impressions` | Number of times ad was shown |
| `clicks` | Number of clicks on the ad |
| `conversions` | Number of completed conversions |
| `revenue` | Revenue generated (£) |

**Full dataset (10 users):**

| user_id | group | impressions | clicks | conversions | revenue |
|---|---|---|---|---|---|
| 1 | A | 10 | 2 | 1 | 20 |
| 2 | A | 8 | 1 | 0 | 0 |
| 3 | A | 12 | 3 | 1 | 25 |
| 4 | A | 9 | 2 | 1 | 22 |
| 5 | A | 11 | 2 | 0 | 0 |
| 6 | B | 10 | 4 | 2 | 40 |
| 7 | B | 9 | 3 | 1 | 30 |
| 8 | B | 13 | 5 | 2 | 50 |
| 9 | B | 8 | 2 | 1 | 28 |
| 10 | B | 12 | 4 | 2 | 45 |

---

## 🧠 Methodology

### 1. Database Setup (SQLite in Jupyter)

```python
!pip install ipython-sql
%load_ext sql
%sql sqlite:///marketing.db
```

```sql
CREATE TABLE campaign_data (
    user_id     INTEGER,
    group_name  TEXT,
    impressions INTEGER,
    clicks      INTEGER,
    conversions INTEGER,
    revenue     INTEGER
);
```

---

### 2. Conversion Rate

```sql
SELECT
    group_name,
    SUM(conversions)                          AS total_conversions,
    SUM(clicks)                               AS total_clicks,
    SUM(conversions) * 1.0 / SUM(clicks)     AS conversion_rate
FROM campaign_data
GROUP BY group_name;
```

| Group | Total Conversions | Total Clicks | Conversion Rate |
|---|---|---|---|
| A | 3 | 10 | **30.0%** |
| B | 8 | 18 | **44.4%** |

---

### 3. Click-Through Rate (CTR)

```sql
SELECT
    group_name,
    SUM(clicks) * 1.0 / SUM(impressions) AS ctr
FROM campaign_data
GROUP BY group_name;
```

| Group | CTR |
|---|---|
| A | **20.0%** |
| B | **34.6%** |

---

### 4. Total Revenue

```sql
SELECT
    group_name,
    SUM(revenue) AS total_revenue
FROM campaign_data
GROUP BY group_name;
```

| Group | Total Revenue |
|---|---|
| A | **£67** |
| B | **£193** |

---

### 5. Statistical Validation — t-Test

To confirm that Variant B's results are statistically significant and not due to chance:

```python
import pandas as pd
from scipy.stats import ttest_ind

data = {
    "group":       ["A","A","A","A","A","B","B","B","B","B"],
    "conversions": [1,  0,  1,  1,  0,  2,  1,  2,  1,  2]
}

df = pd.DataFrame(data)
group_A = df[df["group"] == "A"]["conversions"]
group_B = df[df["group"] == "B"]["conversions"]

t_stat, p_value = ttest_ind(group_A, group_B)
print("t-stat:", t_stat)    # → -2.887
print("p-value:", p_value)  # → 0.020
```

| Metric | Value | Interpretation |
|---|---|---|
| **t-statistic** | -2.887 | B significantly outperforms A |
| **p-value** | 0.020 | ✅ Statistically significant (p < 0.05) |

The difference between Variant A and Variant B is **statistically significant** — the result is not due to random chance.

---

## 📊 Summary of Results

| KPI | Variant A | Variant B | Winner |
|---|---|---|---|
| Conversion Rate | 30.0% | 44.4% | ✅ B (+48%) |
| CTR | 20.0% | 34.6% | ✅ B (+73%) |
| Total Revenue | £67 | £193 | ✅ B (+188%) |
| Statistical Significance | — | p = 0.020 | ✅ B |

**Variant B outperforms Variant A across every KPI, with statistically validated results.**

---

## 💡 Business Insights

- Variant B generated **nearly 3x the revenue** of Variant A (£193 vs £67)
- Variant B's **CTR was 73% higher**, indicating stronger ad creative or targeting
- The **t-test confirms** the performance gap is statistically significant (p = 0.020 < 0.05), making it safe to act on these results
- Conversion rate improvement (+14.4 pp) suggests Variant B better aligns with user intent

---

## 🚀 Business Recommendations

| Action | Rationale |
|---|---|
| **Reallocate budget to Variant B** | Statistically proven higher ROI across all KPIs |
| **Audit Variant A creative** | Identify what elements drove lower engagement |
| **Scale Variant B carefully** | Monitor performance at larger audience sizes before full rollout |
| **Run follow-up A/B tests** | Test new variables (copy, CTA, audience) to continue optimising |

---

## 📂 Repository Structure

```
ab-testing-marketing/
├── ab_testing_analysis.ipynb   # Full SQL + Python analysis notebook
├── campaign_data.csv           # Raw campaign dataset
├── screenshots/                # Tableau dashboard exports
└── README.md
```

---

## 🛠 Skills Demonstrated

![SQL Querying](https://img.shields.io/badge/SQL_Querying-grey?style=flat-square)
![KPI Calculation](https://img.shields.io/badge/KPI_Calculation_(CTR,_CVR,_Revenue)-grey?style=flat-square)
![Statistical Testing](https://img.shields.io/badge/Statistical_Testing_(t--test)-grey?style=flat-square)
![A/B Testing](https://img.shields.io/badge/A/B_Testing_Design-grey?style=flat-square)
![Tableau](https://img.shields.io/badge/Tableau_Dashboards-grey?style=flat-square)
![Business Analysis](https://img.shields.io/badge/Business_Analysis-grey?style=flat-square)

---

## 🎯 Conclusion

This project demonstrates how SQL-based metric computation combined with statistical testing (t-test) can rigorously evaluate A/B marketing experiments. The results clearly show Variant B outperforming across all KPIs with statistical significance — enabling a confident, data-driven budget reallocation decision.

---

> ⚠️ **Note:** Tableau Public dashboards are provided as screenshots in the `screenshots/` folder. SQL queries were executed within Jupyter Notebook using SQLite via `ipython-sql`.
