**# Bank Loan Default Risk Analysis**

## Project Overview
This project is an end-to-end Data Analytics and Business Intelligence project focused on understanding patterns associated with loan defaults and translating findings into practical risk-management actions.
**Tools:** Python, Pandas, Matplotlib, Power BI, DAX
**Business Question:** What borrower and loan characteristics are associated with higher observed default rates, and how can these findings support better risk-management decisions?
## Business Problem
Financial institutions need to understand repayment-risk patterns so that potentially higher-risk applications and existing loans can receive appropriate assessment, structuring and monitoring.

## Project Objectives
- Understand the structure and quality of the loan dataset
- Quantify overall default levels
- Perform exploratory data analysis
- Analyze borrower and loan characteristics
- Identify combinations associated with higher observed default rates
- Analyze defaults outside the identified high-risk segment
- Develop practical business recommendations
- Build a Power BI decision-support dashboard
  
## Dataset
- 255,347 loan records
- 18 original columns
- 29,653 defaults
- 11.61% overall observed default rate
 
### Main Variables
LoanID, Age, Income, LoanAmount, CreditScore, MonthsEmployed, NumCreditLines, InterestRate, LoanTerm, DTIRatio, Education, EmploymentType, MaritalStatus, HasMortgage, HasDependents, LoanPurpose, HasCoSigner, Default
**Target Variable:** Default
- 0 = Non-default
- 1 = Default
  
## Data Quality
- Dataset Size: 255,347 rows × 18 columns
- Missing Values: 0
- Duplicate Rows: 0
- Total Defaults: 29,653
- Overall Default Rate: 11.61%
- 
## Project Workflow
Business Problem → Data Understanding → Data Quality Checks → Exploratory Data Analysis → Risk Segmentation → Portfolio-Wide Analysis → Key Findings → Business Recommendations → Power BI Dashboard

## Exploratory Data Analysis
The analysis examined observed default rates across major borrower and loan dimensions.
- Age: Lowest 25% = 19.15%, Highest 25% = 5.36%
- Income: Low = 17.38%, High = 9.02%
- Loan Amount: Low = 8.25%, High = 15.60%
- Interest Rate: Lowest 25% = 6.58%, Highest 25% = 17.52%
- Credit Score: 300–399 = 13.34%, 800–899 = 9.81%
These are observed historical patterns and do not establish causation.

## High-Risk Segment Analysis
**High-Risk Segment:** Low Income + High Loan Amount + Highest 25% Interest Rate
- Borrowers in Segment: 3,972
- Defaults in Segment: 1,460
- Observed Default Rate: 36.76%
- Overall Default Rate: 11.61%
- Segment Rate Relative to Overall: 3.17×
- Share of All Defaults: 4.92%
- Defaults Outside Segment: 28,193
- Share of Defaults Outside Segment: 95.08%
The identified segment has a substantially higher observed default rate than the overall portfolio, but it represents only a small share of total defaults.

## Deeper Analysis
Within the high-risk segment:
- Employment Type Default Rates: Full-time 31.08%, Part-time 38.37%, Self-employed 34.54%, Unemployed 42.71%
- Loan Purpose Default Rates: Auto 37.76%, Business 38.79%, Education 35.35%, Home 34.48%, Other 37.67%
- DTI Group Default Rates: 34.88%, 36.96%, 37.06%, 38.16%
  
## Portfolio-Wide Analysis
There are 28,193 defaults outside the defined high-risk segment, representing 95.08% of all defaults.
- Age Group: Lowest 25% = 12,575 defaults
- Income Group: Low = 9,635 defaults
- Loan Amount Group: High = 8,501 defaults
- Interest Rate Group: Highest 25% = 9,696 defaults
- DTI Group: Highest 25% = 7,307 defaults
- Employment Type: Unemployed = 8,205 defaults
This shows that defaults are distributed across multiple borrower and loan profiles.

## Key Findings
1. The portfolio contains 255,347 borrowers and 29,653 defaults.
2. The overall observed default rate is 11.61%.
3. The identified high-risk segment has an observed default rate of 36.76%.
4. The segment contains 1,460 defaults and represents 4.92% of all defaults.
5. Most defaults occur outside the identified segment.
6. Age, income, loan amount, interest rate and credit score show meaningful differences in observed default rates.
7. A single risk rule is not sufficient to explain the overall portfolio.
   
## Power BI Dashboard
### Page 1 — Executive Overview
Portfolio-level KPIs and default-rate analysis across major grouped variables.
### Page 2 — Risk Analysis
Analysis of the identified high-risk segment by Employment Type, DTI Group, Loan Purpose and Education.
### Page 3 — Portfolio-Wide Analysis
Analysis of defaults outside the high-risk segment across Age, Income, Loan Amount, Interest Rate, Employment Type and DTI.
### Page 4 — Business Solution
Converts analytical findings into practical risk-management actions.

## Business Recommendations
**Identify → Assess → Structure → Monitor → Validate**
- Identify profiles associated with materially higher observed default rates.
- Assess repayment capacity, existing obligations, DTI, loan amount relative to income and credit history.
- Structure loans appropriately based on verified risk assessment.
- Monitor higher-risk profiles after approval.
- Validate findings using newer data and ongoing performance monitoring.
The identified segment should be treated as an enhanced-review signal rather than an automatic rejection rule.

## Limitations
- Historical analysis describes observed relationships and does not establish causation.
- Grouping continuous variables can hide variation within groups.
- The identified high-risk segment is an analytical segment, not a production underwriting rule.
- Future portfolios may show different relationships.
- Production use would require further validation, governance and fairness assessment.
  
## Conclusion
This project demonstrates an end-to-end analytics workflow connecting Data Quality, Exploratory Data Analysis, Risk Segmentation, Business Insights, Power BI and Business Recommendations.
The analysis identified Low Income + High Loan Amount + Highest 25% Interest Rate as a segment with a substantially higher observed default rate than the portfolio average.
However, most defaults occur outside this segment, supporting a broader multi-factor risk-management approach.

## Project Files
- Bank Loan Dataset.csv — Loan dataset
- Bank Loan Data Python Analysis.ipynb — Python analysis
- Bank Loan Default Risk [DashBoard].pbix — Power BI report
- Bank Loan Default Risk Analysis Report.pdf — Detailed project report
- README.md — Project documentation

  
## Author
**Mallikarjun**
B.Tech — Computer Science & Engineering
**Skills:** Python, Pandas, Matplotlib, Data Cleaning, EDA, Risk Segmentation, Power BI, DAX, Data Visualization, Business Analysis
