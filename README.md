# 📊 Comprehensive Loan Analytics Dashboard – Power BI

![Dashboard-1](https://github.com/bhaskarpal1707/Comprehensive_Loan_Analytics_Dashboard-Power-BI/blob/main/Dashboard%201.png?raw=true)

## 🔍 Project Description:

This project delivers a professional and insightful **Loan Analytics Dashboard** built in **Power BI** using a comprehensive dataset containing financial, behavioral, and demographic data of loan applicants. The dashboard enables data-driven decision-making for banks and financial institutions by analyzing **risk**, identifying **fraud patterns**, and understanding **customer behavior**.

---

## 🎯 Objective:

- Evaluate loan applicants’ **financial risk** using key metrics like credit score and debt ratios.
- Detect **potential fraudulent applications** based on behavior flags like high credit usage and defaults.
- Understand **demographic and behavioral trends** influencing loan approval decisions.
- Build a **professional, interactive Power BI dashboard** for business analysts, loan officers, and auditors.

---

## 🛠️ Technologies Used:

- **Power BI Desktop** (Data Modeling & Visualization)
- **DAX** (Data Analysis Expressions for KPIs and calculations)
- **Power Query (M Language)** for data transformation
- **Python** (for exploratory data analysis in Jupyter)
- Data Format: **CSV**
- Supporting notebook: `EDA.ipynb` (https://github.com/bhaskarpal1707/Loan-Risk-Analyzer)

---
## 📁 EDA Analysis Link: ![](https://github.com/bhaskarpal1707/Loan-Risk-Analyzer)
## 📁 Dataset Overview:

The dataset includes **20,000 loan applicants** and contains:

| Column Name                   | Type     | Description                                  |
|------------------------------|----------|----------------------------------------------|
| `Age`, `CreditScore`, `AnnualIncome`   | Numeric  | Financial & demographic details               |
| `LoanAmount`, `InterestRate`, `LoanApproved` | Numeric  | Loan application info                         |
| `BankruptcyHistory`, `PreviousLoanDefaults` | Integer  | Indicators of credit risk or fraud            |
| `CreditCardUtilizationRate`, `DebtToIncomeRatio` | Float | Credit behavior indicators                    |

---
![Dashboard-1](https://github.com/bhaskarpal1707/Comprehensive_Loan_Analytics_Dashboard-Power-BI/blob/main/Dashboard%202.png?raw=true)

## 📊 Dashboard Structure:

### 🔵 Page 1: Executive Summary (KPIs + Slicers)

**KPI Cards:**
- Average Risk Score
- Average Credit Score
- Avg. Interest Rate
- Avg. Loan Amount
- Applicants with Previous Defaults
- High-Risk Applicants
- Bankruptcy Cases
- Loan Approval Rate
- Fraud-Flagged Applications

**Slicers:**
- Age Group
- Loan Approved
- Marital Status
- Employment Status
- Education Level

---

### 🟠 Page 2: Risk Analysis Visuals

- Risk Score by Education Level
- Risk Score vs. Debt Category (Heatmap)
- Risk Band Distribution (Donut)
- Distribution of Risk Scores (Histogram)

---

### 🟢 Page 3: Customer Behavior & Loan Approval

- Risk Score by Marital Status
- Count of Risk Score by Employment Status
- Loan Purpose vs. Approval Rate (Stacked Bar)
- Education vs. Loan Amount
- Loan Approval % over Age Group (Line Chart)

---

## 📌 DAX Measures Used:

```dax
-- Average Risk Score
AverageRiskScore = AVERAGE('Loan'[RiskScore])

-- Average Credit Score
AverageCreditScore = AVERAGE('Loan'[CreditScore])

-- Average Interest Rate
AverageInterestRate = AVERAGE('Loan'[InterestRate])

-- Average Loan Amount
AverageLoanAmount = AVERAGE('Loan'[LoanAmount])

-- High-Risk Applicants Count
HighRiskApplicants = 
CALCULATE(COUNTROWS('Loan'), 'Loan'[RiskBand] = "High")

-- Bankruptcy Case Count
BankruptcyCases = 
CALCULATE(COUNTROWS('Loan'), 'Loan'[BankruptcyHistory] = 1)

-- Applicants with Previous Defaults
ApplicantsWithDefaults = 
CALCULATE(COUNTROWS('Loan'), 'Loan'[PreviousLoanDefaults] > 0)

-- Loan Approval Rate
LoanApprovalRate = 
DIVIDE(
    CALCULATE(COUNTROWS('Loan'), 'Loan'[LoanApproved] = 1),
    COUNTROWS('Loan')
)

-- Fraud-Flagged Application Count
FraudFlaggedApplications = 
CALCULATE(COUNTROWS('Loan'), 'Loan'[FraudFlag] = 1)

-- Average Credit Inquiries for Fraud-Flagged Applicants
AvgInquiries_FraudOnly = 
CALCULATE(
    AVERAGE('Loan'[NumberOfCreditInquiries]),
    'Loan'[FraudFlag] = 1
)
```
![Dashboard-1](https://github.com/bhaskarpal1707/Comprehensive_Loan_Analytics_Dashboard-Power-BI/blob/main/Dashboard%203.png?raw=true)

## 🔧 Power Query:

```m
-- Age Group
AgeGroup = 
if [Age] < 25 then "<25" 
else if [Age] <= 35 then "25-35" 
else if [Age] <= 45 then "36-45" 
else if [Age] <= 60 then "46-60" 
else "60+"

-- Risk Band (Based on Risk Score)
RiskBand = 
if [RiskScore] < 0.3 then "Low" 
else if [RiskScore] < 0.6 then "Medium" 
else "High"

-- Debt Category (Based on DTI)
DebtCategory = 
if [DebtToIncomeRatio] < 0.3 then "Low" 
else if [DebtToIncomeRatio] < 0.6 then "Medium" 
else "High"

-- Fraud Flag (Suspicious Applications)
FraudFlag = 
if [BankruptcyHistory] = 1 or 
   [PreviousLoanDefaults] > 0 or 
   [CreditCardUtilizationRate] > 0.8 or 
   [NumberOfCreditInquiries] > 5 then 1 
else 0
```


---

### 💡 Business Insights:

```markdown
## 💡 Business Insights

- Applicants with **low credit scores** and **high debt-to-income ratios** tend to have **higher risk scores**.
- A significant number of **fraud-flagged applicants** exhibit:
  - Bankruptcy history
  - High credit card utilization (>80%)
  - More than 5 credit inquiries
- **Loan approval rates** are **higher among applicants** with:
  - Higher education
  - Stable employment
  - Lower financial liabilities
- **Customer behavior trends** like **age group and marital status** strongly influence loan approval and default rates.
```

## ✅ Conclusion:

The **Comprehensive Loan Analytics Dashboard** provides an actionable view into:
- **Loan risk segmentation**
- **Fraud detection automation**
- **Customer behavior insights**

It combines advanced **data modeling**, **Power Query transformations**, and **DAX logic** to help financial institutions make smarter decisions in lending.

> Designed to be **interactive**, **informative**, and **business-ready**, this Power BI project is a complete end-to-end data analytics solution.

```
## 📬 Contact Me

If you found this project helpful or have questions:

- **📧 Email**: bhaskarpal.official@gmail.com  
- **🔗 LinkedIn**: [Bhaskar Pal](https://www.linkedin.com/in/bhaskar-pal-2k02/)
```


