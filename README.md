[README (4).md](https://github.com/user-attachments/files/29429554/README.4.md)
# Credit-Bureau-Analysis# 🏦 Nigerian Credit Bureau — End-to-End Data Analytics Portfolio Project

![Project Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Tools](https://img.shields.io/badge/Tools-Excel%20%7C%20MySQL%20%7C%20Power%20BI-blue)
![Records](https://img.shields.io/badge/Records-10%2C000-orange)
![Period](https://img.shields.io/badge/Period-2022--2024-lightgrey)

---

## 📌 Project Overview

This is an end-to-end data analytics portfolio project simulating a real-world credit bureau analysis for a Nigerian financial institution. The project covers the full analyst workflow — from synthetic data generation and data cleaning, through SQL analysis, to an executive Power BI dashboard.

The dataset contains **10,000 customer credit records** across **10 Nigerian states** and **3 reporting years (2022–2024)**, with intentional data quality issues embedded for cleaning practice.

> **Dashboard Title:** *A Portfolio Under Pressure*
> A single-page executive dashboard telling the story of a credit portfolio with a 33% default rate, a regional crisis in Rivers State, and 785 customers on the brink of defaulting.

---

## 🎯 Business Problem

A Nigerian credit bureau needs to understand the health of its loan portfolio, identify the highest-risk customers and regions, and make data-driven recommendations to reduce default rates and delinquency exposure.

**Key questions answered:**
- What is the overall default rate and how does it vary by state?
- Which loan types carry the highest delinquency rates?
- Who are the highest-risk customers not yet in default?
- How does credit score relate to default probability?
- Which regions and loan types require immediate intervention?

---

## 🗂️ Project Structure

```
nigerian-credit-bureau/
│
├── data/
│   ├── credit_bureau_dataset.csv          # Raw dataset (with quality issues)
│   └── credit_bureau_dataset_cleaned.csv  # Cleaned dataset
│
├── docs/
│   ├── credit_bureau_project_guide.pdf    # Data dictionary, KPIs, SQL guide
│   └── credit_bureau_cleaning_log.pdf     # Data cleaning documentation
│
├── sql/
│   └── credit_bureau_queries.sql          # All 12 SQL queries (beginner → advanced)
│
├── dashboard/
│   └── credit_bureau_visualization.pbix   # Power BI dashboard file
│
└── README.md
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Python (pandas, numpy)** | Synthetic data generation 
| **Excel (Power Query)** | data cleaning |
| **MySQL Workbench** | SQL analysis & business question answering |
| **Power BI** | Interactive executive dashboard |
| **reportlab** | PDF documentation generation |

---

## 📊 Dataset Overview

| Attribute | Detail |
|---|---|
| Total Records | 10,000 (after cleaning) |
| Columns | 22 |
| Geographic Coverage | 10 Nigerian States |
| Loan Types | Personal, Mortgage, Auto, Business, Student, Payday |
| Reporting Period | January 2022 — December 2024 |
| Default Rate | 33.3% |

### Columns
`Customer_ID` · `Age` · `Gender` · `State` · `Employment_Status` · `Annual_Income` · `Credit_Score` · `Loan_Type` · `Loan_Amount` · `Outstanding_Balance` · `Monthly_Payment` · `Number_of_Open_Accounts` · `Number_of_Late_Payments` · `Credit_Utilization_Rate` · `Debt_to_Income_Ratio` · `Account_Age_Months` · `Credit_Inquiries_Last_12_Months` · `Default_Status` · `Delinquency_Status` · `Risk_Category` · `Report_Month` · `Report_Year`

---

## 🧹 Data Cleaning

The raw dataset contained **5 intentional data quality issues**:

| Issue | Detail | Resolution |
|---|---|---|
| Duplicate records | 150 fully duplicated rows | Removed with `drop_duplicates()` |
| Missing numeric values | ~3–4% nulls across 4 columns | Median imputation |
| Missing categorical values | 331 nulls in Employment_Status | Filled as 'Unknown' |
| Inconsistent Gender formatting | 8 variants (M, male, MALE etc.) | Standardised to Male/Female |
| Inconsistent Employment_Status | 9 variants (EMPLOYED, employed etc.) | Standardised to 5 categories |

> Full cleaning decisions and justifications documented in `credit_bureau_cleaning_log.pdf`

**Why median over mean?**
Annual_Income and Monthly_Payment contain outliers that inflate the mean significantly (Monthly_Payment mean: ₦155,732 vs median: ₦36,337). Median imputation preserves the true central value without distortion.

---

## 🔍 SQL Analysis

12 queries ranging from beginner to advanced, covering:

- **Beginner:** Total customers, default rate breakdown, risk category counts, avg credit score by loan type
- **Intermediate:** States above national default average, delinquency by loan type, pre-default customer identification, duplicate detection
- **Advanced:** YoY credit score trends, window functions for exposure ranking, composite risk scoring with NTILE(), loan type risk profiling with CTEs

### Key SQL Findings

| Finding | Result |
|---|---|
| Overall default rate | 33.31% |
| Rivers State default rate | 63.15% — nearly 2x the national average |
| Payday loan delinquency | 52.19% of customers are not current |
| High Risk customers | 67.6% of portfolio |
| Pre-default customers | 785 customers with utilization >70% and DTI >0.5 |
| Highest exposure state | Lagos — ₦11.7bn total outstanding |

---

## 📈 Power BI Dashboard
<img width="969" height="548" alt="Credit Bureau Dashboard" src="https://github.com/user-attachments/assets/e67ef523-82ec-40fa-ac73-f4d7b721b954" />


**Title:** *A Portfolio Under Pressure*

A single-page executive dashboard with 6 visuals and a recommendations section:

| Zone | Visual | Insight |
|---|---|---|
| KPI Cards | 5 metric cards | Portfolio health at a glance |
| Zone 1 | Bar chart — Default Rate by State | Rivers State is the epicentre of default risk at 63.1% |
| Zone 2 | Donut chart — Risk Category | 67.95% of customers are High Risk |
| Zone 3 | Table — Pre-Default Watchlist | 785 customers at the brink of defaulting |
| Zone 4 | Stacked bar — Delinquency by Loan Type | Personal and Mortgage loans drive the most delinquencies |
| Zone 5 | Bar chart — Credit Score vs Default Rate | Lower credit scores are directly linked to higher default rates |
| Recommendations | Text box | 3 actionable interventions derived from the data |

**DAX measures included:** Default Rate %, High Risk %, State Default Rate, Pre-Default Flag, Risk Adjusted Exposure, YoY Score Change, and more.

---

## 💡 Key Insights & Recommendations

1. **Rivers State requires immediate intervention** — a 63.1% default rate, nearly double the 33.3% national average, signals a regional economic shock requiring tighter lending criteria and active collections.

2. **Personal and Mortgage loans drive the most delinquencies** — these two loan types account for the largest share of delinquent accounts and should be the primary focus for collections and underwriting review.

3. **785 customers are on the brink of defaulting** — customers with credit utilization above 70% and DTI above 0.5 who have not yet defaulted represent an immediate intervention opportunity. Proactive outreach now is cheaper than collections later.

---

## 🚀 How to Use This Project

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/nigerian-credit-bureau.git
```

2. **Explore the data**
```python
import pandas as pd
df = pd.read_csv('data/credit_bureau_dataset_cleaned.csv')
df.head()
```

3. **Run the SQL queries**
- Import `credit_bureau_dataset_cleaned.csv` into MySQL
- Open `sql/credit_bureau_queries.sql` and run queries in MySQL Workbench

4. **Open the dashboard**
- Open `dashboard/credit_bureau_visualization.pbix` in Power BI Desktop
- Refresh the data source to point to your local CSV path

---

## 👩🏽‍💻 About

**Oluwabusola Oyenuga** — Data Analyst

This project was built as part of an ongoing data analytics portfolio series documented on LinkedIn.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/your-linkedin)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/yourusername)

---

*Dataset is synthetic and generated for portfolio purposes. All customer records are fictional.*
