{\rtf1\ansi\ansicpg1252\cocoartf2867
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;\f1\froman\fcharset0 Times-Roman;}
{\colortbl;\red255\green255\blue255;\red0\green0\blue0;}
{\*\expandedcolortbl;;\cssrgb\c0\c0\c0;}
\margl1440\margr1440\vieww48540\viewh18920\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # \uc0\u55357 \u56522  Marketing A/B Testing & Campaign Analytics (SQL & Tableau Public)\
\
This project analyzes A/B testing experiments to evaluate marketing campaign performance and optimize conversion rates. SQL was used to compute key metrics, and Tableau Public was used to build dashboards for monitoring ROI and engagement.\
\
---\
\
## \uc0\u55357 \u56520  Project Overview\
\
The objective of this project is to compare two marketing campaign variants (A vs B) and determine which performs better using key performance indicators such as conversion rate, click-through rate (CTR), and revenue.\
\
This project simulates a real-world marketing analytics workflow combining data analysis, experimentation, and business decision-making.\
\
---\
\
## \uc0\u55356 \u57263  Key Objectives\
\
- **A/B Testing Analysis**: Compare campaign variants and measure performance differences  \
- **SQL Analysis**: Calculate key marketing metrics  \
- **Data Visualization**: Build dashboards in Tableau Public  \
- **Business Insights**: Translate results into actionable recommendations  \
\
---\
\
## \uc0\u55357 \u56514  Dataset\
\
The dataset simulates campaign performance with the following variables:\
\
- `user_id`  \
- `group_name` (A/B test group)  \
- `impressions`  \
- `clicks`  \
- `conversions`  \
- `revenue`  \
\
---\
\
## \uc0\u55358 \u56800  Methodology\
\
### SQL Analysis (Jupyter Notebook)\
- Created a SQLite database inside Jupyter  \
- Executed SQL queries using `ipython-sql`  \
- Aggregated results by campaign group  \
- Calculated:\
  - **Conversion Rate** = conversions / clicks  \
  - **CTR (Click Through Rate)** = clicks / impressions  \
  - **Total Revenue**\
\
### A/B Testing Evaluation\
- Compared Variant A vs Variant B  \
- Identified which variant drives higher engagement and revenue  \
\
### Data Visualization (Tableau Public)\
- Built dashboards to visualize:\
  - Conversion rate comparison  \
  - Revenue performance  \
  - Campaign effectiveness  \
\
---\
\
## \uc0\u55357 \u56522  Key Results\
\
- Variant B achieved a higher conversion rate than Variant A  \
- Variant B generated higher total revenue  \
- Increased engagement (clicks and conversions) led to improved campaign performance  \
\
---\
\
## \uc0\u55357 \u56568  Visualizations\
\
### Conversion Rate Comparison\
![Conversion Rate](screenshots/conversion_rate_chart.png)\
\
### Revenue Dashboard\
![Revenue Dashboard](screenshots/revenue_dashboard.png)\
\
---\
\
## \uc0\u55357 \u56481  Business Insights\
\
- Campaign performance is strongly influenced by user engagement  \
- Variant B consistently outperforms Variant A across key metrics  \
- Higher conversion rates directly translate into increased revenue  \
\
---\
\
## \uc0\u55357 \u56960  Business Recommendations\
\
- Allocate more budget to Variant B to maximize ROI  \
- Analyze differences between variants to replicate successful strategies  \
- Continue running A/B tests to further optimize campaigns  \
\
---\
\
## \uc0\u55357 \u57056  Tools Used\
\
- SQL (SQLite via Jupyter Notebook)  \
- Tableau Public  \
- Data Analysis & Visualization  \
\
---\
\
## \uc0\u9888 \u65039  Notes\
\
- Tableau Public dashboards are not included as `.twbx` files  \
- Visual outputs are provided as screenshots in the `screenshots/` folder  \
- SQL queries were executed within Jupyter Notebook using SQLite  \
\
---\
\
## \uc0\u55357 \u56514  Repository Structure\
\
````\
\pard\pardeftab720\partightenfactor0

\f1 \cf0 \expnd0\expndtw0\kerning0
\outl0\strokewidth0 \strokec2 ab-testing-marketing/\
\uc0\u9500 \u9472 \u9472  ab_testing_analysis.ipynb\
\uc0\u9500 \u9472 \u9472  campaign_data.csv\
\uc0\u9500 \u9472 \u9472  screenshots/\
\uc0\u9492 \u9472 \u9472  README.md\
\
````\
---\
\
## \uc0\u55356 \u57263  Conclusion\
\
This project demonstrates how A/B testing combined with SQL analysis can be used to evaluate marketing performance, optimize campaigns, and support data-driven decision-making in real business scenarios.}