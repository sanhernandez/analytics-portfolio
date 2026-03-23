# Sales & Revenue Forecasting using Regression (Python + Excel)

This project builds a regression-based forecasting model to predict revenue trends and support campaign planning and KPI tracking. The model was developed in Python and replicated in Excel to simulate real business workflows.

## Project Overview
The goal of this project is to combine technical modeling with business thinking by forecasting sales/revenue using a simple regression model. It demonstrates how predictions can inform real business decisions.

### Key Objectives
1. **Forecasting (Prediction)**: Predict future revenue based on historical data.
2. **Regression Modeling**: Use Linear Regression with features like Time and Marketing Spend.
3. **Business Insights**: Provide actionable recommendations based on model results.

## Dataset
- Columns: `Date`, `Revenue`, `Marketing_Spend`
- Period: Jan 2022 – Jun 2023
- Source: Simulated for project purposes

## Methodology
1. **Data Preparation**
   - Convert `Date` to datetime format
   - Sort data by date
   - Create a `Time` variable to capture trend
2. **Modeling**
   - Linear Regression: `Revenue = f(Time + Marketing_Spend)`
   - Fit model using historical data
   - Generate predictions for next 6 months
3. **Visualization**
   - Actual vs Predicted Revenue line chart
   - Future forecast overlay

## Forecast Results
Predicted revenue for the next 6 months shows a steady increase:

| Month | Predicted Revenue |
|-------|-----------------|
| 2023-07 | 27,955 |
| 2023-08 | 28,928 |
| 2023-09 | 30,020 |
| 2023-10 | 30,992 |
| 2023-11 | 32,084 |
| 2023-12 | 33,415 |

## Executive Insights & Recommendations

### Revenue Forecast Overview 📈
- Predicted revenue for the next 6 months grows from **27,955 → 33,415**, representing ~20% increase.
- Marketing spend is strongly correlated with revenue: higher investment drives higher sales.
- Overall trend is positive, but occasional dips indicate other external factors might influence revenue.

### Key Insights
1. **Consistent growth trend**: Revenue steadily increases month-over-month.
2. **Marketing effectiveness**: Months with higher marketing spend result in higher revenue.
3. **Seasonal fluctuations**: Some months (e.g., May 2022) show temporary drops, suggesting other variables at play.

### Recommendations for Business Action
- **Optimize marketing budget**: Allocate funds to months where marketing ROI is historically higher.
- **Track forecast vs actual**: Monitor monthly performance to adjust campaigns in real time.
- **Investigate anomalies**: Identify and mitigate factors causing temporary revenue dips.
- **Plan for growth**: Use predicted revenue trends to set realistic sales targets and KPI goals.

## Skills Demonstrated
- Python & Pandas for data processing
- Linear Regression modeling
- Excel replication of regression and forecast
- Data visualization & business insights

## Repo Structure
