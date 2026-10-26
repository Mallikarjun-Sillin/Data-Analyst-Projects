# MedTourEasy — Patient Conversion & Provider Performance Intelligence
An end-to-end data analytics and machine learning portfolio project focused on patient journey analysis, treatment completion, provider benchmarking, operational drop-off, and financial performance.

## Project Overview
Healthcare service providers need visibility into patient journeys to understand where cases stall, which drop-off reasons are recorded most frequently, how providers compare, and how revenue and service costs are distributed.

This project analyses patient journey and treatment outcome data to build a business intelligence dashboard, investigate operational bottlenecks, compare provider performance, and evaluate whether initial inquiry information can predict recorded patient drop-off.

**The primary objective is to turn raw healthcare operations data into actionable, evidence-based business insights.**

> This is a portfolio analytics project. It is not a clinical decision system, and its findings do not establish causal relationships or audited financial results.

## Project Objectives
- Analyse patient journey stages and treatment completion.
- Measure recorded patient drop-off and examine the documented reasons.
- Compare provider performance using patient volume, satisfaction, treatment outcomes, and financial metrics.
- Analyse revenue, service cost, and gross margin.
- Explore differences across lead sources, treatment categories, and patient segments.
- Evaluate machine learning models for predicting recorded patient drop-off.
- Recommend improvements to status tracking, follow-up ownership, and operational reporting.

## Technology Stack
| Technology | Purpose |
|---|---|
| Python | Data analysis and machine learning |
| Pandas and NumPy | Data manipulation and numerical analysis |
| Scikit-learn | Model training and evaluation |
| SQL / SQLite | Structured data storage and querying |
| Power BI | Interactive business intelligence dashboard |
| Jupyter Notebook / Google Colab | Analysis and experimentation |
| Git and GitHub | Version control and project documentation |

## Dashboard Overview

The Power BI report contains four analytical pages.

### 1. Executive Overview
Provides a high-level view of patient volume, recorded drop-off, treatment completion, completion rate, and revenue. It highlights the distribution of patient records by current journey stage, lead source, and recorded drop-off reason.

### 2. Patient Conversion Analysis
Examines patient journey stages, treatment completions by treatment category, patient volume by lead source, and recorded drop-off reasons.

### 3. Provider Performance Analysis
Compares providers by patient volume, patient satisfaction, regional distribution, treatment completion, and recorded revenue. These comparisons support operational review rather than definitive judgments about provider quality.

### 4. Revenue & Financial Analysis
Analyses recorded revenue, service costs, gross margin, and revenue distribution across providers and treatment categories.

## Dataset Summary

The analysis uses the original project source files.
| Dataset | Records | Purpose |
|---|---:|---|
| `patient_journey.csv` | 1,500 | Patient demographics, inquiry details, current stage, status flags, and financial fields |
| `provider_master.csv` | 30 | Provider profiles, specialties, and reference performance metrics |
| `communication_logs.csv` | 6,025 | Communication events, response information, and follow-up activity |
| `treatment_outcomes.csv` | 554 | Treatment outcomes, revenue, service costs, length of stay, and readmission information |
| `country_reference.csv` | 12 | Country reference information |
| `data_dictionary.csv` | 67 | Field definitions and examples |

The original source files were used to validate key counts and financial totals. The dataset represents the supplied project data and should not be interpreted as a complete or audited view of real-world healthcare operations.

## Key Findings

### Patient Journey and Conversion
- **1,500** patient records were analysed.
- **350 patients (23.3%)** were flagged as recorded drop-offs.
- **554 patients (36.9%)** were marked as treatment-completed.
- **596 patients (39.7%)** were neither flagged as drop-off nor marked treatment-completed. These records are treated as unresolved or status-uncertain rather than automatically classified as successful conversions.
- Consultation and First Response had observed recorded drop-off rates of approximately **39.7%** and **39.0%**, respectively.

### Recorded Drop-off Reasons
The most frequently recorded reasons among the 350 flagged drop-offs were:
| Recorded reason | Cases |
|---|---:|
| No follow-up | 66 |
| Cost concern | 62 |
| Response delay | 60 |
| Chose competitor | 45 |
| Travel constraints | 30 |

These findings suggest reviewing follow-up ownership, response-time performance, and early cost communication. They are descriptive observations, not proof that any single factor caused a patient to drop off.

### Financial Analysis
| Metric | Recorded total |
|---|---:|
| Revenue | ₹248,325,245 |
| Service cost | ₹136,810,889 |
| Gross margin | ₹111,514,356 |

Gross margin is calculated as recorded revenue minus recorded service cost. It does not account for other operating expenses, taxes, or overheads and should not be interpreted as net profit.

### Provider Performance
Provider comparisons include patient volume, treatment completion, follow-up activity, satisfaction, revenue, service cost, and gross margin where supported by the source data.
Results should be interpreted alongside patient volume, specialty, case mix, and data completeness. Higher recorded revenue or completion alone does not establish better clinical quality.

## Machine Learning Evaluation
Three classification baselines were evaluated for predicting the recorded drop-off flag:
- Logistic Regression
- Random Forest
- Gradient Boosting

The modelling approach used an 80/20 stratified train-test split and inquiry-time features intended to be available when a patient first makes an inquiry. Later journey information was excluded to reduce temporal data leakage.
The tested features included country, age group, gender, treatment category, lead source, budget band, and medical urgency.

**Model results were not strong enough for production use.**
- ROC-AUC scores ranged from **0.489 to 0.516**, close to random ranking.
- Logistic Regression identified some drop-off cases but generated many false-positive alerts.
- Random Forest missed most actual drop-off cases.
- Gradient Boosting predicted no positive drop-off cases in the held-out test set.

These results demonstrate the importance of evaluating precision, recall, confusion matrices, and class-specific performance instead of relying on accuracy alone.
No model from this experiment is recommended for automated patient-level prioritisation.

## Business Recommendations
1. **Clarify patient statuses:** Separate completed, active/in-progress, and confirmed-drop-off cases.
2. **Create an unresolved-case queue:** Track the current stage, assigned owner, last contact, next action, and days since last contact.
3. **Improve response-time monitoring:** Define response targets and escalation rules for overdue first responses.
4. **Standardise drop-off reasons:** Use structured reason codes and monitor missing or inconsistent classifications.
5. **Review provider performance with context:** Consider patient volume, specialty, case mix, and data completeness.
6. **Maintain financial definitions:** Document how revenue, service cost, and gross margin are calculated.
7. **Revisit predictive modelling after data improvements:** Validate labels and features before training and testing new models.

## Repository Contents
The `MedTourEasy-Patient-Intelligence` folder contains the following project deliverables:
| File | Description |
| `MedTourEasy_Patient_Intelligence_Dashboard.pbix` | Power BI dashboard with four analytical pages |
| `MedTourEasy_Report.pdf` | Detailed analytics report, findings, model evaluation, and recommendations |
| `MedTourEasy_google_colab.ipynb` | Google Colab notebook containing the project's analysis and experiments |
| `README.md` | Project overview, documentation, findings, and limitations |

The source datasets were used for the analysis. Their availability in this repository depends on the files actually committed to GitHub.

## How to Review the Project
1. Open `MedTourEasy_Report.pdf` to read the methodology, verified findings, model evaluation, and recommendations.
2. Open `MedTourEasy_Patient_Intelligence_Dashboard.pbix` using Microsoft Power BI Desktop to explore the dashboard.
3. Open `MedTourEasy_google_colab.ipynb` in Google Colab or Jupyter Notebook to inspect the analytical workflow. Re-running the notebook may require the original source datasets and the relevant Python libraries.
4. Use the four dashboard pages to explore executive metrics, patient conversion, provider performance, and financial results.

## Limitations
- The dataset contains 1,500 patient records and a limited number of positive drop-off labels.
- The 596 unresolved records make the target definition unsuitable for treating every non-drop-off record as a confirmed success.
- Provider comparisons are observational and may be affected by case mix, specialty, volume, and missing data.
- Recorded drop-off reasons may reflect the completeness of operational data entry.
- Financial totals are reconciled to the supplied source data but are not audited financial statements.
- The tested machine learning models did not demonstrate reliable predictive performance and are not production-ready.
- The analysis does not establish causation or support clinical treatment decisions.

## Conclusion

MedTourEasy demonstrates an end-to-end analytics workflow spanning data validation, patient journey analysis, provider benchmarking, financial reporting, dashboard development, and machine learning evaluation.

The key takeaway is that improving patient status definitions, follow-up tracking, and operational data quality should take priority over deploying predictive models that have not demonstrated reliable performance.

The project showcases the application of **Python, SQL, Power BI, data analysis, and machine learning evaluation** to a practical business intelligence problem.


**Project:** MedTourEasy — Patient Conversion & Provider Performance Intelligence  
**Project type:** Data Analytics, Business Intelligence, and Machine Learning Evaluation  
**Year:** 2026

