# Customer Churn Prediction

## Project Overview

This project analyses telecom customer data to identify factors associated with customer churn and develop machine-learning models to predict customers who are likely to leave.

The project covers:

- Data inspection and cleaning
- Exploratory data analysis (EDA)
- Feature preparation and encoding
- Logistic Regression
- Random Forest
- Model evaluation
- Model interpretation
- Classification threshold tuning
- Business recommendations

The analysis was completed using Python and scikit-learn.

---

## Dataset

The dataset contains **7,043 telecom customers** and **21 variables**.

The variables include:

- Customer demographics
- Internet and telecom services
- Contract details
- Payment methods
- Monthly charges
- Total charges
- Customer churn status

The target variable is `Churn`, which indicates whether a customer stayed with or left the company.

### Churn Distribution

- Customers who stayed: **5,174 (73.46%)**
- Customers who churned: **1,869 (26.54%)**

Approximately one-quarter of the customers in the dataset churned.

---

## Data Cleaning

The dataset was inspected for missing values, data types and inconsistencies.

During the analysis, **11 blank values** were identified in the `TotalCharges` column.

The column was converted to numeric format using `pd.to_numeric()` with invalid values converted to missing values. The resulting missing values were then handled, and the dataset was checked again to confirm that no missing values remained.

---

## Exploratory Data Analysis

Several customer characteristics were analysed to understand their relationship with churn.

### Contract Type

Customers on month-to-month contracts showed higher churn than customers on one-year and two-year contracts.

This indicates that month-to-month customers are an important group to consider when developing customer-retention strategies.

### Tenure

Customers who churned had a lower average tenure than customers who stayed.

- Average tenure for customers who stayed: **37.57 months**
- Average tenure for customers who churned: **17.98 months**

### Monthly Charges

Customers who churned had higher average monthly charges than customers who stayed.

- Customers who stayed: approximately **$61.27**
- Customers who churned: approximately **$74.44**

### Internet Service

Churn varied across internet-service types.

Fiber optic customers had a higher observed churn rate than DSL and customers without internet service.

This is an observed association and does not establish that the type of internet service itself causes churn.

### Payment Method

Electronic-check customers showed a higher observed churn rate than customers using the other payment methods analysed.

This may be useful for further investigation into the payment experience and customer retention.

### Online Security and Tech Support

Customers with Online Security and Tech Support showed lower observed churn than customers without these services.

These relationships were treated as associations rather than causal effects.

---

## Machine Learning

Two classification models were developed:

- Logistic Regression
- Random Forest

The dataset was divided into training and testing sets using an **80/20 stratified split**.

Stratification was used to maintain a similar proportion of churned and non-churned customers in both datasets.

---

## Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC-AUC

### Model Performance

| Model | Accuracy | ROC-AUC |
|---|---:|---:|
| Logistic Regression | 80.7% | 0.842 |
| Random Forest | 79.0% | 0.826 |

Logistic Regression produced the higher ROC-AUC in this analysis and was used for the subsequent threshold-tuning analysis.

---

## Model Interpretation

The Logistic Regression coefficients were analysed to understand which features were associated with higher or lower predicted churn probability.

Examples of features associated with higher predicted churn included:

- Fiber optic internet service
- Higher TotalCharges
- Streaming TV
- Streaming Movies
- Multiple Lines
- Paperless Billing
- Electronic Check

Features associated with lower predicted churn included:

- Longer tenure
- One-year contracts
- Two-year contracts
- Online Security
- Tech Support
- Dependents

The model coefficients describe associations within the trained model and should not be interpreted as evidence that these factors directly cause or prevent churn.

---

## Threshold Tuning

The default classification threshold of **0.50** was compared with lower thresholds.

At the default threshold:

- Churn recall: **57%**

At a threshold of **0.30**:

- Churn recall: **75%**

The 0.30 threshold was selected as a reasonable business trade-off for this project because it identifies more of the customers who actually churned, while also producing more false-positive predictions.

At the 0.30 threshold:

- True negatives: **774**
- False positives: **261**
- False negatives: **92**
- True positives: **282**

This demonstrates how changing the classification threshold changes the balance between identifying churners and generating false alerts.

---

## Business Recommendations

Based on the analysis, the following areas could be considered for further investigation:

1. **Focus on month-to-month customers**  
   Explore suitable retention strategies and incentives for customers on month-to-month contracts.

2. **Encourage longer-term contracts**  
   Customers on one-year and two-year contracts showed lower observed churn.

3. **Promote relevant support services**  
   Customers with Online Security and Tech Support showed lower observed churn.

4. **Investigate fiber optic customers**  
   The analysis identified higher observed churn among fiber optic customers. Further investigation could examine pricing, service quality and customer experience.

5. **Investigate electronic-check customers**  
   Further analysis could examine whether payment experience or other customer characteristics are associated with the higher observed churn rate.

---

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- VS Code
- Git / GitHub

---

## Project Structure

```text
customer-churn-prediction/
│
├── data/
├── images/
├── models/
├── notebooks/
│   └── Customer_Churn_Prediction.ipynb
├── src/
├── README.md
└── requirements.txt

