# 📊 Sales Forecasting using Regression Analysis

This project develops a revenue forecasting model using historical data on time trends and marketing spend. The objective is to predict future revenue and support data-driven business decision-making.

---

## 📈 Project Overview

The goal of this project is to build a regression-based model that forecasts revenue while combining technical modelling with business insights. It demonstrates how predictive analytics can support strategic decision-making.

---

## 🎯 Key Objectives

- **Forecasting**: Predict future revenue based on historical data  
- **Regression Modelling**: Apply multiple linear regression using time and marketing spend  
- **Business Insights**: Translate model outputs into actionable recommendations  

---

## 🔧 Tools & Technologies

- Python (Pandas, NumPy, Scikit-learn)  
- Matplotlib  
- Regression Modelling  

---

## 📂 Dataset

- Columns: `Date`, `Revenue`, `Marketing_Spend`  
- Frequency: Monthly  
- Source: Simulated dataset  

---

## 🧠 Methodology

### Data Preparation
- Converted date to datetime format  
- Sorted data chronologically  
- Created a time trend variable  

### Model Development
- Applied **multiple linear regression** using:
  - Time (trend)  
  - Marketing Spend  
- Trained the model to predict revenue  

### Model Evaluation
- Compared predicted vs actual values  
- Calculated performance metrics:
  - **MAE:** ~1,016  
  - **RMSE:** ~2,121  
- Analysed prediction error distribution  

### Forecasting
- Generated revenue forecasts for the next 6 months  
- Visualised actual vs predicted vs future trends  

---

## 📊 Forecast Results

| Month   | Predicted Revenue |
|--------|------------------|
| 2023-07 | 27,955 |
| 2023-08 | 28,928 |
| 2023-09 | 30,020 |
| 2023-10 | 30,992 |
| 2023-11 | 32,084 |
| 2023-12 | 33,415 |

---

## 📈 Key Insights

- Revenue shows a **positive growth trend over time**  
- Marketing spend is **positively correlated with revenue**  
- Variability suggests influence of additional external factors  

---

## 💡 Business Recommendations

- Optimise marketing investment based on performance trends  
- Track forecast vs actual results to improve accuracy  
- Investigate anomalies to refine the model  
- Use forecasts to support KPI planning and budgeting  

---

## 📊 Visualisations

- Actual vs Predicted Revenue  
- Forecasted Revenue Trend  
- Error Distribution  

---

## 🛠 Skills Demonstrated

- Python (Pandas, Scikit-learn)  
- Regression Modelling  
- Model Evaluation (MAE, RMSE)  
- Data Visualisation  
- Business Analysis  

---

## 📂 Repository Structure
````
sales-forecasting/
├── sales_forecasting.ipynb
├── dataset.csv
├── excel_model.xlsx
├── screenshots/
└── README.md
````

---

## 🎯 Conclusion

This project demonstrates how regression models can be used to generate revenue forecasts, evaluate model performance, and support data-driven business decisions.
