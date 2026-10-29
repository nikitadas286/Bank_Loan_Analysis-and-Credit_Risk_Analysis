# 🏦 Bank Loan & Credit Risk Analytics

##  Project Overview

- Analyze customer financial profiles and loan characteristics.
- Identify loan default patterns across different borrower segments.
- Examine the impact of income, employment history, interest rates, and loan grades on credit risk.
- Investigate relationships between loan amounts, loan purposes, and repayment status.
- Identify high-risk borrower categories through exploratory data analysis.
- Provide data-driven insights to support better lending decisions and credit risk management.

##  Objectives

- Analyze borrowers' financial profiles and loan characteristics.
- Explore the distribution of defaulted and non-defaulted loans.
- Compare default patterns across income levels, credit grades, interest rates, and loan purposes.
- Examine the relationship between loan size relative to income and default status.
- Identify useful risk indicators and translate findings into business insights for credit assessment.

##  Dataset and Column Guide

The project uses a **single CSV file**, not separate customer, loan, and payment tables. The dataset contains these 12 attributes:

| Column | Meaning |
|---|---|
| `person_age` | Borrower's age |
| `person_income` | Borrower's annual income |
| `person_home_ownership` | Housing status, such as rent, own, or mortgage |
| `person_emp_length` | Employment length in years |
| `loan_intent` | Purpose of the loan |
| `loan_grade` | Assigned loan credit grade |
| `loan_amnt` | Loan principal amount |
| `loan_int_rate` | Loan interest rate (%) |
| `loan_status` | Loan outcome: 0 = non-default, 1 = default |
| `loan_percent_income` | Loan amount as a fraction of annual income |
| `cb_person_default_on_file` | Whether a prior default is recorded in credit history |
| `cb_person_cred_hist_length` | Length of credit history in years |

##  Tools and Skills

   1. Python.
   2. Pandas.
   3. Numpy.
   4. Data Cleaning & Preprocessing.
   5. Missing Value Treatment.
   6. Exploratory Data Analysis(EDA).
   7. Data Visulization (Matplotlib & Seaborn).
      
##  Analysis Workflow

### Step 1 — Data Loading & Understanding

- Imported NumPy and Pandas.
- Loaded `credit_risk_dataset.csv`.
- Inspected the first rows, shape, column names, data types, and descriptive statistics.
- Separated categorical and numerical features.
- Reviewed the `loan_status` target and its class counts.

**Initial result:** The notebook reports **32,581 records and 12 columns**.

### Step 2 — Data Cleaning & Preprocessing

- Checked for missing values in `person_emp_length` and `loan_int_rate`.
- Filled missing values in these two numerical columns using **mean imputation**.
- Checked for and removed **165 exact duplicate rows**.
- Flagged ages outside **18–100** and employment lengths below zero or exceeding `person_age - 18`.
- Replaced flagged age and employment values with missing values, then filled them using column means.
- Checked for invalid income, loan amount, interest rate, and target-status values; the notebook notes no invalid values in these checks.

### Step 3 — Exploratory Data Analysis (EDA)

The notebook answers **eight business questions** using a variety of plots:

| # | Business question | Chart / library | What it investigates |
|---|---|---|---|
| 1 | What percentage of bank loans have defaulted? | Count plot · Seaborn | Distribution of loan outcomes |
| 2 | How are loan amounts distributed among borrowers? | Histogram · Matplotlib | Typical loan sizes and skewness |
| 3 | How does borrower income differ between defaulted and non-defaulted loans? | Box plot · Seaborn | Median income and variation by outcome |
| 4 | Which loan grades have the highest default rates? | Bar plot · Seaborn | Credit grade risk segmentation |
| 5 | How do interest rates vary between defaulted and non-defaulted loans? | Violin plot · Seaborn | Interest-rate density and quartiles |
| 6 | Which loan purposes have the highest default rates? | Horizontal bar chart · Matplotlib | Risk differences across loan purposes |
| 7 | What is the relationship between loan-to-income ratio and loan default risk? | Scatter plot · Seaborn | Income, relative loan size, and outcomes |
| 8 | Which numerical factors are most strongly correlated with loan defaults? | Correlation heatmap · Seaborn | Linear associations between numerical variables |


##  Key Findings

1. **Loan-to-Income Ratio:** An important indicator of financial burden, helping assess potential loan default risk.

2. **Loan Grade:** Helps distinguish borrowers across different credit risk categories and identify higher-risk loan segments.

3. **Interest Rate:** An important lending factor that may be associated with borrower creditworthiness and loan default risk.

4. **Borrower Income & Employment:** Provide useful insights into financial stability and repayment capacity.

5. **Credit History:** Previous loan defaults can help identify borrowers requiring closer credit risk assessment.


##  Business Insights and Recommendations

1. **Evaluate affordability:** Consider loan-to-income ratio alongside income, existing liabilities, and repayment capacity.
2. **Monitor credit-grade segments:** Compare default rates across grades and review higher-risk segments more closely.
3. **Assess interest-rate affordability:** Higher rates are associated with defaults in this sample; investigate the underlying borrower risk and loan pricing context.
4. **Review loan-purpose trends:** Explore why debt consolidation, medical, and home improvement loans show higher default rates in the sample.
5. **Use multiple indicators:** Avoid relying on a single demographic or financial variable when evaluating risk; validate any proposed decision rules with additional data and fairness checks.

## 🏁 Final Conclusion

This project demonstrates an end-to-end workflow for transforming raw loan data into interpretable credit risk insights. The notebook highlights **loan-to-income ratio, loan grade, and interest rate** as important factors to investigate, with borrower income and credit history providing additional context. The results can inform further credit risk research and portfolio monitoring, but real-world lending decisions require more rigorous validation.
