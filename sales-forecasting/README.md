# 📊 Sales Forecasting using Regression Analysis

> *Revenue forecasting model using multiple linear regression — combining predictive analytics with business intelligence to support data-driven decision-making.*

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)

---

## 📈 Project Overview

This project builds a **multiple linear regression model** to forecast monthly revenue using historical time trends and marketing spend data. It bridges technical modelling with actionable business recommendations.

---

## 🎯 Key Objectives

- **Forecasting** — Predict future revenue based on historical data
- **Regression Modelling** — Apply multiple linear regression using time trend and marketing spend as predictors
- **Business Insights** — Translate model outputs into strategic recommendations

---

## 🔧 Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy, Scikit-learn) | Data processing & modelling |
| Matplotlib | Data visualisation |
| SciPy | Statistical testing (t-tests) |
| Excel | Business-ready forecast model |

---

## 📂 Dataset

| Column | Description |
|---|---|
| `Date` | Monthly timestamp (YYYY-MM) |
| `Revenue` | Monthly revenue |
| `Marketing_Spend` | Monthly marketing investment |

- **Frequency:** Monthly
- **Source:** Simulated dataset

**Sample data:**

| Date | Revenue | Marketing_Spend |
|---|---|---|
| 2022-01 | 12,000 | 2,000 |
| 2022-02 | 13,500 | 2,200 |
| 2022-03 | 12,800 | 2,100 |
| 2022-04 | 15,000 | 2,500 |
| 2022-05 | 6,000 | 2,700 |

---

## 🧠 Methodology

### 1. Data Preparation

```python
import pandas as pd

df = pd.read_csv("sales_data.csv")
df['Date'] = pd.to_datetime(df['Date'])
df = df.sort_values('Date')
df['Time'] = range(len(df))  # Trend variable
```

- Converted dates to datetime format
- Sorted data chronologically
- Created a numeric time trend variable as a predictor

---

### 2. Model Development

```python
from sklearn.linear_model import LinearRegression

X = df[['Time', 'Marketing_Spend']]
y = df['Revenue']

model = LinearRegression()
model.fit(X, y)

df['Predicted_Revenue'] = model.predict(X)
```

**Predictors used:**
- `Time` — captures the revenue growth trend over time
- `Marketing_Spend` — captures the impact of marketing investment on revenue

---

### 3. Model Evaluation

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error
import numpy as np

mae  = mean_absolute_error(y, df['Predicted_Revenue'])
rmse = np.sqrt(mean_squared_error(y, df['Predicted_Revenue']))

print("MAE:", mae)    # → 1015.65
print("RMSE:", rmse)  # → 2121.32
```

| Metric | Value | Interpretation |
|---|---|---|
| **MAE** | ~1,016 | Average absolute prediction error |
| **RMSE** | ~2,121 | Penalises larger errors more heavily |

Prediction errors were also analysed through an **error distribution histogram**, confirming a roughly symmetric spread around zero.

---

### 4. Statistical Validation (A/B Test)

To validate the model's predictive power, a **t-test** was applied to compare conversion performance between two groups:

```python
from scipy.stats import ttest_ind

t_stat, p_value = ttest_ind(group_A, group_B)
# t-stat: -2.887
# p-value: 0.020
```

| Result | Value |
|---|---|
| t-statistic | -2.887 |
| p-value | 0.020 |
| Significant? | ✅ Yes (p < 0.05) |

The difference between groups is **statistically significant**, confirming that the observed patterns are not due to chance.

---

### 5. Revenue Forecasting — Next 6 Months

```python
import numpy as np

future_time = np.arange(len(df), len(df) + 6)
future_marketing = [5500, 5700, 6000, 6200, 6500, 7000]

future_df = pd.DataFrame({
    'Time': future_time,
    'Marketing_Spend': future_marketing
})

future_df['Predicted_Revenue'] = model.predict(future_df)
```

**Forecast results:**

| Month | Marketing Spend | Predicted Revenue |
|---|---|---|
| 2023-07 | 5,500 | 27,955 |
| 2023-08 | 5,700 | 28,928 |
| 2023-09 | 6,000 | 30,020 |
| 2023-10 | 6,200 | 30,992 |
| 2023-11 | 6,500 | 32,084 |
| 2023-12 | 7,000 | 33,415 |

---

## 📊 Visualisations

1. **Actual vs Predicted Revenue** — Model fit against historical data
2. **Actual vs Predicted + Forecast Trend** — Extended view including 6-month projections
3. **Error Distribution** — Histogram of prediction residuals

---

## 📊 Key Insights

- Revenue shows a **consistent positive growth trend** over time
- Marketing spend has a **positive correlation with revenue**
- Remaining variability suggests the influence of **additional external factors** not captured in the model
- The 6-month forecast projects revenue growing from **~27,955 to ~33,415**

---

## 💡 Business Recommendations

- **Optimise marketing investment** — Scale spend strategically based on the forecasted revenue-to-spend relationship
- **Track forecast vs actuals** — Monitor monthly deviations to continuously improve model accuracy
- **Investigate anomalies** — Analyse outlier months (e.g., May 2022: Revenue 6,000 despite high spend) to refine the model
- **Use forecasts for KPI planning** — Incorporate 6-month projections into budgeting and performance target-setting

---

## 📂 Repository Structure

```
sales-forecasting/
├── sales_forecasting.ipynb   # Full analysis notebook
├── dataset.csv               # Raw dataset
├── excel_model.xlsx          # Business-ready Excel forecast model
├── screenshots/              # Visualisation exports
└── README.md
```

---

## 🛠 Skills Demonstrated

![Regression Modeling](https://img.shields.io/badge/Regression_Modeling-grey?style=flat-square)
![Statistical Testing](https://img.shields.io/badge/Statistical_Testing_(t--test)-grey?style=flat-square)
![Model Evaluation](https://img.shields.io/badge/Model_Evaluation_(MAE,_RMSE)-grey?style=flat-square)
![Data Visualisation](https://img.shields.io/badge/Data_Visualisation-grey?style=flat-square)
![Business Analysis](https://img.shields.io/badge/Business_Analysis-grey?style=flat-square)
![Excel Modelling](https://img.shields.io/badge/Excel_Modelling-grey?style=flat-square)

---

## 🎯 Conclusion

This project demonstrates how multiple regression models can generate reliable revenue forecasts, quantify model performance through error metrics, and support strategic business decisions. The inclusion of statistical validation (t-test) and an Excel replica makes the output accessible to both technical and non-technical stakeholders.
