# Loan-Default-Prediction-Using-Machine-Learning


# Project Description

This project focuses on predicting whether a loan applicant will default on loan repayment. Using financial and demographic information of applicants, machine learning models classify customers as Default or Not Default, helping financial institutions make informed and risk-aware lending decisions.

# Objective

To develop a machine learning model that predicts whether a loan applicant is likely to default or not default, enabling banks and financial institutions to minimize credit risk and improve loan approval decisions.

# Data Collection

The dataset was downloaded from:
 https://www.opendatabay.com/data/financial/22adb045-3090-4e6b-a76f-ca9771b8d4e0037

# Data Description

The dataset contains financial, demographic, and loan-application-related features that help assess an applicant’s creditworthiness.

Total records: 148,670

Total features: 34

Target variable: Status (Default / Not Default)

# Feature Overview

| No | Feature                   | Description                      |
|----|---------------------------|----------------------------------|
| 1  | ID                        | Unique loan application ID       |
| 2  | year                      | Year of application (2019 only)  |
| 3  | loan_limit                | Conforming / Non-conforming loan |
| 4  | Gender                    | Male / Female / Joint            |
| 5  | approv_in_adv             | Pre-approval status              |
| 6  | loan_type                 | Loan type (type1, type2, type3)  |
| 7  | loan_purpose              | Purpose of loan (p1–p4)          |
| 8  | Credit_Worthiness         | Credit category (l1 / l2)        |
| 9  | open_credit               | Open credit lines                |
| 10 | business_or_commercial    | Business/commercial loan         |
| 11 | loan_amount               | Loan amount                      |
| 12 | rate_of_interest          | Interest rate                    |
| 13 | Interest_rate_spread      | Rate spread                      |
| 14 | Upfront_charges           | Origination charges              |
| 15 | term                      | Loan duration (months)           |
| 16 | Neg_ammortization         | Negative amortization            |
| 17 | interest_only             | Interest-only loan               |
| 18 | lump_sum_payment          | Lump-sum option                  |
| 19 | property_value            | Property value                   |
| 20 | construction_type         | Property structure               |
| 21 | occupancy_type            | Primary / Secondary / Investment |
| 22 | Secured_by                | Home / Land                      |
| 23 | total_units               | Number of units                  |
| 24 | income                    | Applicant income                 |
| 25 | credit_type               | Credit bureau                    |
| 26 | Credit_Score              | Credit score                     |
| 27 | co-applicant_credit_type  | Co-applicant credit source       |
| 28 | age                       | Age group                        |
| 29 | submission_of_application | Application channel              |
| 30 | LTV                       | Loan-to-Value ratio              |
| 31 | Region                    | Geographic region                |
| 32 | Security_Type             | Direct / Indirect                |
| 33 | Status (Target)           | 1 = Default, 0 = Not Default     |
| 34 | dtir1                     | Debt-to-Income ratio             |




# Data Preprocessing
1. Dropping Unimportant Columns

Dropped ID and year (constant value: 2019).

2️. Handling Missing Values

Categorical columns: Filled using mode

Numerical columns: Filled using median (robust to outliers)

3️. Handling Outliers

Detected using boxplots and IQR method

Extreme values were capped

Term column was excluded from outlier treatment because it represents valid loan durations (e.g., 120, 240, 360 months)

4️. Encoding Categorical Variables

Applied One-Hot Encoding using pd.get_dummies()

Avoids multicollinearity and converts categories into binary form

Target variable mapped as:

df['Status'] = df['Status'].map({1: 'Default', 0: 'Not Default'})

# Models Used
1️⃣ Logistic Regression

Purpose:
A linear classification model used as a baseline to estimate the probability of default.

Hyperparameters Tuned:

Regularization strength (C)

Penalty (l2)

Class weight

Evaluation Summary:

Performs very well for Not Default cases

Moderate ability to detect Default cases

Struggles with class imbalance, as default cases are fewer

Logistic Regression gives good overall performance but finds it harder to correctly identify defaulters in an imbalanced dataset.

2️⃣ Random Forest Classifier

Model Description:
Random Forest is an ensemble-based model that builds multiple decision trees and combines their predictions to capture complex, non-linear patterns.

Hyperparameters Tuned:

Number of trees (n_estimators)

Maximum depth (max_depth)

Class weighting

Evaluation Summary:

Achieved very high performance on the test dataset

Demonstrated strong ability to separate Default and Not Default classes

Significantly outperformed Logistic Regression

Note: Extremely high accuracy suggests the presence of strong feature patterns in the dataset and highlights the need for careful validation to avoid data leakage in real-world applications.

✅ Conclusion

Logistic Regression served as a strong baseline model.

Random Forest provided superior performance by capturing non-linear relationships.

Feature engineering and preprocessing played a crucial role in model effectiveness.

This project demonstrates how machine learning can assist financial institutions in minimizing credit risk.
