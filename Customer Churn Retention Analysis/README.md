# Customer Churn & Retention Analysis

## 1. Project Overview

Customer churn is a major challenge for subscription-based businesses. Understanding why customers leave and identifying customers at risk of leaving can help businesses improve retention, optimize marketing strategies, and make data-driven decisions.

This project combines Exploratory Data Analysis (EDA), Machine Learning, and Power BI to analyze customer churn, predict churn risk, identify important churn-related factors, and develop targeted customer retention strategies.

Using the IBM Telco Customer Churn dataset, a Random Forest classification model estimates customer churn probabilities and segments customers into different risk categories.

## 2. Project Objectives

- Analyze customer churn and retention patterns.
- Identify customer segments with higher churn rates.
- Examine relationships between tenure, contract type, services, billing, and churn.
- Develop a machine learning model to predict customer churn.
- Evaluate model performance using classification metrics.
- Segment customers into low-, medium-, and high-risk categories.
- Develop actionable customer retention recommendations.
- Build interactive Power BI dashboards for business reporting.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data analysis and machine learning |
| Pandas | Data cleaning and manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Exploratory data visualization |
| Scikit-learn | Preprocessing, model training, and evaluation |
| Google Colab | Development environment |
| Power BI | Interactive dashboards and business intelligence |
| Git and GitHub | Version control and project documentation |

## 4. Dataset Description

**Dataset:** IBM Telco Customer Churn

The dataset contains customer demographic information, subscribed services, contract details, billing information, tenure, and churn status.

- Total customer records: 7,043
- Original dataset columns: 21
- Target variable: `Churn`
- Problem type: Binary classification

### Important Features

| Feature | Description |
|---|---|
| `gender` | Customer gender |
| `SeniorCitizen` | Indicates whether the customer is a senior citizen |
| `Partner` | Whether the customer has a partner |
| `Dependents` | Whether the customer has dependents |
| `tenure` | Number of months the customer has stayed |
| `InternetService` | Type of internet service |
| `OnlineSecurity` | Online security subscription status |
| `TechSupport` | Technical support subscription status |
| `Contract` | Customer contract type |
| `PaymentMethod` | Customer payment method |
| `MonthlyCharges` | Monthly amount charged |
| `TotalCharges` | Total amount charged |
| `Churn` | Indicates whether the customer left the company |

## 5. Project Workflow

1. **Data Collection:** Load the IBM Telco Customer Churn dataset.
2. **Data Cleaning:** Inspect data types, missing values, and inconsistent formats.
3. **Exploratory Data Analysis:** Analyze churn distribution and relationships between customer characteristics and churn.
4. **Feature Engineering:** Convert the target variable into a numerical format for classification.
5. **Data Preprocessing:** Standardize numerical features and encode categorical features.
6. **Model Development:** Train a Random Forest classifier.
7. **Model Evaluation:** Evaluate predictions using accuracy, precision, recall, F1-score, ROC-AUC, and a confusion matrix.
8. **Risk Segmentation:** Classify customers into risk categories based on predicted churn probabilities.
9. **Dashboard Development:** Build Power BI dashboards to communicate analytical findings.
10. **Business Recommendations:** Translate findings into potential customer retention strategies.

## 6. Data Cleaning and Preprocessing

The following preprocessing steps were implemented:

- Inspected the dataset for missing values and inconsistent data types.
- Converted `TotalCharges` from text to a numerical data type.
- Handled 11 blank `TotalCharges` values associated with zero-tenure customers by assigning zero.
- Encoded the churn target as `0` for retained customers and `1` for churned customers.
- Standardized numerical features using `StandardScaler`.
- Encoded categorical features using `OneHotEncoder`.
- Combined preprocessing steps using a `ColumnTransformer` and a scikit-learn pipeline.

This preprocessing approach supports consistent transformations during model training and prediction.

## 7. Exploratory Data Analysis

The analysis investigated customer churn across the following dimensions:

- Overall churn and retention distribution.
- Customer tenure and churn behavior.
- Contract types and churn rates.
- Monthly charges and total charges.
- Internet service and additional service subscriptions.
- Payment methods and billing preferences.
- Customer characteristics associated with churn.

### Key Findings

- Historical churn rate: 26.54%.
- Historical retention rate: 73.46%.
- Month-to-month contracts are an important segment for churn-risk analysis.
- Customer tenure is one of the most important features in the trained model.
- The absence of online security and technical support is associated with higher churn risk in the model's feature-importance analysis.

These findings describe patterns in the dataset and do not establish that individual factors directly cause customer churn.

## 8. Machine Learning Model

### Random Forest Classifier

A Random Forest classifier was selected to estimate customer churn probabilities and identify patterns associated with customer departures.

The model uses class weighting to account for the imbalance between churned and retained customers.

### Model Configuration

```python
RandomForestClassifier(
    n_estimators=200,
    max_depth=10,
    min_samples_leaf=5,
    class_weight="balanced",
    random_state=42,
    n_jobs=-1
)
```

### Model Development Approach

- Split the dataset into training and testing sets.
- Applied numerical scaling and categorical encoding.
- Trained a Random Forest classifier with balanced class weights.
- Used five-fold stratified cross-validation with out-of-fold predictions to inform classification threshold selection.
- Selected a classification threshold of 0.55.
- Evaluated predictions using standard classification metrics.

## 9. Model Evaluation

The following results were recorded for the test set at the selected classification threshold.

| Metric | Result |
|---|---:|
| Accuracy | 77.43% |
| Churn Precision | 56.01% |
| Churn Recall | 69.79% |
| Churn F1-score | 62.14% |
| ROC-AUC | 84.19% |

### Confusion Matrix

| Actual Class | Predicted Retained | Predicted Churn |
|---|---:|---:|
| Retained | 830 | 205 |
| Churn | 113 | 261 |

### Interpretation

- **Accuracy:** Proportion of all predictions classified correctly.
- **Precision:** Proportion of predicted churners who actually churned.
- **Recall:** Proportion of actual churners identified by the model.
- **F1-score:** Harmonic mean of precision and recall.
- **ROC-AUC:** Measures how well the model distinguishes between churned and retained customers across classification thresholds.

The model identifies a substantial proportion of customers who churned, making it a useful starting point for customer retention analysis.

**Evaluation limitation:** The test set was examined during model comparisons, feature-importance analysis, and threshold selection. Therefore, these results should be treated as development-stage estimates rather than an unbiased final assessment. A genuinely untouched test set should be used for final validation.

## 10. Customer Risk Segmentation

Customers were grouped according to their predicted churn probabilities.

| Risk Category | Probability Range | Customers | Percentage |
|---|---|---:|---:|
| Low Risk | Below 0.30 | 3,316 | 47.08% |
| Medium Risk | 0.30 to below 0.55 | 1,438 | 20.42% |
| High Risk | 0.55 and above | 2,289 | 32.50% |
| **Total** | | **7,043** | **100%** |

### Business Interpretation

**Low Risk:** Maintain customer satisfaction and monitor engagement.

**Medium Risk:** Investigate potential dissatisfaction and provide relevant support.

**High Risk:** Prioritize retention outreach and investigate possible contract, billing, and service-related concerns.

These categories represent estimated risk rather than certainty about future behavior. Observed churn rates from historical records should not be interpreted as guaranteed future outcomes.

## 11. Power BI Dashboard

The Power BI report contains four dashboard pages.

### Page 1: Executive Overview

Presents high-level business metrics, including total customers, churned customers, retained customers, and overall churn rate.

### Page 2: Customer Churn Analysis

Examines churn patterns across contract types, tenure, services, payment methods, and customer characteristics.

### Page 3: Churn Risk and Retention

Highlights customer risk segments and supports the prioritization of potential retention activities.

### Page 4: Model Performance

Presents classification metrics and confusion-matrix results to communicate model performance and limitations.

## 12. Business Recommendations

1. **Prioritize high-risk customers:** Use predicted churn probabilities to identify customers who may benefit from retention outreach.
2. **Review month-to-month contracts:** Evaluate whether suitable longer-term plans and incentives could improve customer retention.
3. **Improve early customer engagement:** Monitor customers with short tenure and provide effective onboarding support.
4. **Investigate service-related concerns:** Examine the experiences of customers without online security or technical support.
5. **Evaluate pricing and billing:** Investigate whether monthly charges and payment experiences contribute to customer dissatisfaction.
6. **Measure retention campaign outcomes:** Compare customer outcomes before and after retention interventions.
7. **Monitor model performance:** Reassess predictive performance as customer behavior and business conditions change.

These recommendations should be tested against real business outcomes before their effectiveness is assumed.

## 13. Project Deliverables

| File | Description |
|---|---|
| `README.md` | Project documentation |
| `customer_churn_risk_predictions.csv` | Customer-level churn probability and risk predictions |
| `model_evaluation_results.csv` | Model evaluation metrics |
| `customer_risk_summary.csv` | Summary of customer risk segments |
| `retention_strategy.csv` | Retention strategy recommendations |
| `customer_churn_project_summary.csv` | Summary of project findings and metrics |
| `customer_churn_random_forest.pkl` | Saved trained model or pipeline |
| `customer_churn_project_outputs.zip` | Packaged project outputs |

The Google Colab notebook, Power BI report, and detailed project report can also be included in the repository if available.

## 14. Limitations

- The dataset represents historical customer behavior and may not reflect current customer patterns.
- Predictive associations do not establish causation.
- Model performance may change when applied to new customers or different business conditions.
- Classification threshold selection involves a trade-off between identifying churners and generating false alarms.
- The reported test metrics may be optimistic because the test set informed model and threshold decisions.
- Risk thresholds should be evaluated against retention campaign capacity and the relative costs of false positives and missed churners.

## 15. Future Improvements

- Evaluate the final model using a genuinely untouched test set.
- Compare Random Forest with Logistic Regression and Gradient Boosting.
- Tune hyperparameters using cross-validation.
- Evaluate precision-recall trade-offs and probability calibration.
- Add reproducible training and evaluation scripts.
- Connect Power BI to refreshed customer data for ongoing monitoring.
- Measure the effectiveness of retention campaigns using controlled experiments.

## 16. Skills Demonstrated

- Data cleaning and preprocessing
- Exploratory data analysis
- Feature engineering
- Python and Pandas
- Scikit-learn pipelines
- Random Forest classification
- Imbalanced classification and class weighting
- Classification metrics and threshold selection
- Customer churn prediction
- Customer risk segmentation
- Power BI dashboard development
- Business intelligence and data-driven recommendations
- GitHub documentation and project organization

## 17. Author

**Mallikarjun**  
BTech Computer Science and Engineering

This project demonstrates the practical application of data analytics, machine learning, and business intelligence to a customer retention problem.
