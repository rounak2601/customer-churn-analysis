# 📉 Customer Churn Analysis & Prediction

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python) ![MySQL](https://img.shields.io/badge/MySQL-8.0-orange?logo=mysql) ![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi) ![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-red?logo=scikit-learn) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> An end-to-end data analytics project analyzing customer churn behavior in a telecom company — from SQL-based EDA to machine learning prediction and an interactive Power BI dashboard.

---

## 👤 Author

**Rounak Kumar Tilante**
- GitHub: [@rounak2601](https://github.com/rounak2601)
- LinkedIn: [Rounak Tilante](https://www.linkedin.com/in/rounak-tilante-a9719b257/)

---

## 📌 Project Overview

Customer churn — when a customer stops using a service — is one of the most critical business problems in the telecom industry. This project identifies **why customers churn**, **who is most at risk**, and **what actions can reduce churn**, backed by data.

**Dataset:** IBM Telco Customer Churn Dataset (Kaggle)
**Records:** 7,032 customers | 21 features

---

## 🎯 Key Business Insights

| Finding | Insight |
|---|---|
| 📊 Overall Churn Rate | **26.58%** of customers churned |
| 📋 Contract Risk | Month-to-month customers churn at **42.71%** vs 2.85% for two-year contracts — a **15x difference** |
| 🕐 Tenure Risk | **47.68%** of customers churn in their first 12 months |
| 🔧 Tech Support | Customers without tech support churn at **41.65%** vs 15.20% |
| 🌐 Internet Service | **69.4%** of churned customers used Fiber optic |
| 💳 Payment Method | Electronic check users have the highest churn count (**2,365**) |
| 💰 Revenue at Risk | **$2.86M** total revenue lost | **$139.13K** monthly revenue at risk |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **MySQL** | Database setup, data loading, EDA queries |
| **Python (pandas, seaborn, matplotlib)** | Data cleaning, feature engineering, visualization |
| **scikit-learn** | Logistic Regression & Random Forest models |
| **Power BI** | Interactive dashboard |
| **Jupyter Notebook** | End-to-end analysis environment |

---

## 📁 Project Structure

```
customer-churn-analysis/
│
├── churn_analysis.ipynb        ← Main Jupyter Notebook (EDA + ML)
├── churn_final.csv             ← Cleaned dataset
├── Churn_Analysis_Dashboard.pbix ← Power BI Dashboard
│
├── images/
│   ├── churn_distribution.png
│   ├── churn_by_contract.png
│   ├── tenure_vs_churn.png
│   ├── correlation_heatmap.png
│   └── feature_importance.png
│
└── README.md
```

---

## 🗄️ Phase 1 — SQL Analysis (MySQL)

Loaded 7,032 records into MySQL and ran exploratory queries to find business insights.

**Key queries performed:**
- Overall churn rate calculation
- Churn segmentation by contract type, tenure, internet service, tech support
- Revenue at risk quantification
- High-risk customer identification

```sql
-- Churn rate by contract type
SELECT 
    Contract,
    COUNT(*) AS total,
    SUM(CASE WHEN Churn = 'Yes' THEN 1 ELSE 0 END) AS churned,
    ROUND(SUM(CASE WHEN Churn = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2) AS churn_rate
FROM telco_churn
GROUP BY Contract
ORDER BY churn_rate DESC;
```

**Result:** Month-to-month: 42.71% | One year: 11.28% | Two year: 2.85%

---

## 🐍 Phase 2 — Python Analysis & ML Model

### Data Cleaning
- Fixed `TotalCharges` blank values
- Encoded categorical variables using LabelEncoder
- Scaled features using StandardScaler

### Visualizations
- Churn distribution bar chart
- Churn by contract type
- Tenure vs churn box plot
- Correlation heatmap

### Machine Learning

| Model | Accuracy | AUC Score |
|---|---|---|
| Logistic Regression | 78.54% | **0.83** ⭐ |
| Random Forest | 79.25% | 0.81 |

**Top churn drivers (Random Forest Feature Importance):**
1. TotalCharges
2. MonthlyCharges
3. Tenure
4. Contract type
5. Tech Support

---

## 📊 Phase 3 — Power BI Dashboard

Interactive dashboard with:
- 4 KPI cards (Total Customers, Churned, Churn Rate, Revenue at Risk)
- 6 interactive charts
- Contract type slicer filter
- Dark professional theme

---

## 💡 Business Recommendations

Based on the analysis, the following actions are recommended:

**1. Target Month-to-Month Customers**
Offer discounts to convert month-to-month customers to annual plans. This alone could reduce churn by up to 40%.

**2. Improve Onboarding (First 12 Months)**
Nearly half of all churn happens in the first year. A structured onboarding program with check-ins at 30/60/90 days could significantly improve early retention.

**3. Bundle Tech Support**
Customers without tech support churn at 2.7x the rate. Offering bundled tech support at signup could reduce this gap.

**4. Target Electronic Check Users**
With 2,365 churned customers using electronic check, switching them to automatic payment methods could reduce churn friction.

**Estimated Impact:** Targeting the top 500 high-risk customers could retain approximately **$94,000 in annual revenue**.

---

## 🚀 How to Run This Project

```bash
# 1. Clone the repository
git clone https://github.com/rounak2601/customer-churn-analysis.git
cd customer-churn-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn mysql-connector-python sqlalchemy jupyter

# 3. Launch Jupyter Notebook
jupyter notebook churn_analysis.ipynb
```

---

## 📈 Results Summary

- Built an end-to-end churn analysis pipeline from raw CSV to ML model
- Achieved **AUC of 0.83** using Logistic Regression on 7,032 customer records
- Identified top 5 churn drivers using Random Forest feature importance
- Quantified **$2.86M revenue at risk** from churned customers
- Delivered an interactive Power BI dashboard for business stakeholders

---

*This project was built as part of a data analyst portfolio. Dataset sourced from IBM Sample Data on Kaggle.*
