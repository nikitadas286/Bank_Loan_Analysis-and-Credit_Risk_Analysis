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

  
##  Dataset Information

- **Dataset Name:** Credit Risk Dataset
- **Source:** Kaggle
- **Dataset Link:** [Credit Risk Dataset](https://www.kaggle.com/datasets/laotse/credit-risk-dataset)
- **File Name:** `credit_risk_dataset.csv`
- **File Format:** CSV (Comma-Separated Values)
- **Total Records:** 32,581
- **Total Columns:** 12
- **Target Variable:** `loan_status`
- **Target Categories:**
  - `0` — Non-defaulted Loan
  - `1` — Defaulted Loan

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

### Q1. What percentage of bank loans have defaulted?

<img width="1015" height="612" alt="1 count plot" src="https://github.com/user-attachments/assets/fececaea-2162-4cdd-bc7f-0313f01e138a" />


### Observation: 
- The count plot compares defaulted and non-defaulted loans. The calculated default rate shows the percentage of loans that defaulted in the dataset.

### Conclusion: 
- The default rate provides a baseline for understanding the dataset's credit risk.
- Banks can use default-rate monitoring to identify portfolio deterioration and evaluate whether additional risk controls are needed.

### Q2. How are loan amounts distributed among borrowers?

<img width="1175" height="610" alt="2 histogram" src="https://github.com/user-attachments/assets/e7314628-d148-47b0-a66c-4e6d0c8ce624" />


### Observation:
- Most loan amounts are concentrated between 2,000 and 15,000, with the highest frequencies around 4,000–5,000 and 9,000–10,000 (approximately 3,200 loans per peak bin).
- The distribution is right-skewed.
### Conclusion:
- Small and medium-sized loans dominate the portfolio, indicating higher demand for lower loan amounts.

### Q3. How does borrower income differ between defaulted and non-defaulted loans?

<img width="1206" height="706" alt="3 box plot" src="https://github.com/user-attachments/assets/824d7288-5663-410d-a78b-55f56b6046b9" />


### Observation:
- Non-default borrowers (0) have a higher median annual income compared to default borrowers (1).
### Conclusion:
- Lower annual income is associated with higher loan default risk, suggesting that income is an important factor in credit risk assessment.
- Banks should evaluate borrowers' income stability and repayment capacity before approving loans to minimize potential defaults.

### Q4. Which loan grades have the highest default rates?

<img width="1133" height="567" alt="4 bar plot" src="https://github.com/user-attachments/assets/cbfbded4-108e-4cc9-91f5-6d06820d85ac" />


### Observation:
- Grade A has the lowest default rate, followed by Grade B and Grade C.
- Default rates increase significantly for Grade D , E, F, and G , indicating a strong relationship between credit grade and loan default.
### Conclusion:
- Credit grade is a strong indicator of loan default risk, with lower credit grades showing substantially higher default rates.
- Banks should prioritize Grades A–C for lower-risk lending and apply stricter credit assessments and risk controls for Grades D–G to minimize financial losses.

### Q5. How do interest rates vary between defaulted and non-defaulted loans?

<img width="1032" height="662" alt="5 violin plot" src="https://github.com/user-attachments/assets/f7006ebc-af9c-4a2c-aeee-ff27ec6f4131" />


### Observation:
- Non-default borrowers have a median interest rate of approximately 11%, with most rates concentrated between 8% and 13%.
- Default borrowers have a higher median interest rate of approximately 13.5%, with significant concentrations around 12% and 16%.
### Conclusion:
- Higher interest rates are associated with increased loan default risk, indicating that interest rate is an important factor in credit risk analysis.
- Banks should carefully assess borrowers' repayment capacity and interest rate affordability to reduce defaults and improve loan recovery.

### Q6. Which loan purposes have the highest default rates?

<img width="1357" height="627" alt="6 barh" src="https://github.com/user-attachments/assets/e50663b0-497c-4c45-9838-b29f78618ab5" />


### Observation:
- Debt consolidation has the highest default rate at 28.7%, followed by Medical (26.8%) and Home Improvement (26.2%).
- Venture loans have the lowest default rate at 14.9%, followed by Education (17.3%) and Personal (19.9%).
### Conclusion:
- Loan purpose is an important factor in credit risk assessment, with debt consolidation, medical, and home improvement loans showing higher default risk.
- Banks should apply stricter repayment capacity assessments for high-risk loan purposes and consider loan purpose when developing lending strategies to minimize defaults.

### Q7. What is the relationship between loan-to-income ratio and loan default risk?

<img width="1213" height="653" alt="7 scatter plot" src="https://github.com/user-attachments/assets/03b9aa2f-2135-44ae-af25-6b85706dacde" />


### Observation:
- Lower-income borrowers show higher loan-to-income ratios, reaching approximately 0.8 (80%), while higher-income borrowers generally have ratios below 0.1 (10%).
- Both default and non-default cases appear at higher ratios, while income outliers extend up to approximately 6 million.
### Conclusion:
- Loan-to-income ratio decreases as borrower income increases, indicating a lower relative debt burden for higher-income borrowers.
- Banks should assess loan-to-income ratios alongside income and repayment capacity to identify financially vulnerable borrowers and manage credit risk effectively.

### Q8. Which numerical factors are most strongly correlated with loan defaults?

<img width="1182" height="766" alt="8 heatmap" src="https://github.com/user-attachments/assets/20bac7ba-ad00-4cba-8829-45e3f0e6ac1e" />


### Observation:
- Loan-to-income ratio (0.38) and interest rate (0.32) show the strongest positive correlations with loan default (loan_status).
- Annual income (-0.15) has a negative correlation with default, while age (-0.022) and employment length (-0.075) show very weak relationships.
- Age and credit history length (0.88) have the strongest overall correlation, followed by loan amount and loan-to-income ratio (0.57).
### Conclusion:
- Loan-to-income ratio and interest rate are the strongest numerical indicators of loan default risk in this heatmap.
- Banks should prioritize repayment capacity, interest rates, and borrower income during credit risk assessment to support better lending decisions and reduce potential defaults.

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

## Author

**Nikita Das**

- [GitHub](https://github.com/nikitadas286)
- [LinkedIn](https://www.linkedin.com/in/nikita-laki-das-91786b2b3/)
