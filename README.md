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

1. ID :
A unique identification number assigned to each loan application.

3. year :
The year in which the loan application was submitted. [2019]

5. loan_limit :
Indicates whether the loan amount exceeds the conforming limit (e.g., conforming (cf) / non-conforming (ncf) ). ['cf', 'ncf']

6. Gender :
Applicant’s gender information [Male, Female, Joint].

7. approv_in_adv :
Specifies whether the applicant received pre-approval for the loan [pre / nopre].

8. loan_type :
Type of loan applied [type1, type2, type3].

9. loan_purpose :
Purpose of the loan (e.g., home purchase, refinancing, etc.) ['p1' /  'p4' /  'p3' /  'p2']

10. Credit_Worthiness :
Category representing applicant’s creditworthiness [l1 / l2].

11. open_credit :
Indicates whether the borrower has open credit lines ['nopc' /  'opc']

12. business_or_commercial :
Whether the loan is for business or commercial use. ['nob/c' /  'b/c']

13. loan_amount :
Total amount of loan applied for (numeric values).

14. rate_of_interest :
Interest rate applicable to the loan. (numeric values)

15. Interest_rate_spread :
Difference between the interest rate and market benchmark. (numeric values).

16. Upfront_charges :
Additional fees charged at the loan origination. (numeric values).

17. term :
Total loan term duration in months (numeric values). (e.g., 180, 240, 360).

18. Neg_ammortization :
Indicates whether negative amortization is allowed ['not_neg' /  'neg_amm' nan]

19. interest_only :
Specifies whether the loan allows interest-only payments. ['not_int' /  'int_only']

20. lump_sum_payment :
Whether a lump-sum payment option is included. ['not_lpsm' / 'lpsm']

21. property_value :
Value of the property against which the loan is issued. (numeric values)

22. construction_type :
Structure type of the property ['sb', 'mh']

23. occupancy_type :
Indicates whether the applicant will occupy the property [primary / secondary / investment].

24. Secured_by :
Whether the loan is secured by home or land. 

25. total_units :
Number of housing units in the property (1U, 2U, 3U, 4U).

26. income :
Applicant’s monthly or annual income. (numeric values)

27. credit_type :
Source of credit score (CRIF, CIBIL, EXP, EQUI).

28. Credit_Score :
Numerical credit score of the applicant.

29. co-applicant_credit_type :
Denotes credit source for the co-applicant. ['CIB' 'EXP']

30. age :
Applicant’s age group (e.g., 25–34, 35–44, etc.)

31. submission_of_application :
Channel via which the application was submitted (institution / not institution). ['to_inst' 'not_inst']

32. LTV (Loan-to-Value Ratio) :
Ratio of loan amount to property value — important for risk assessment. (numeric value)

33. Region :
Geographic region (North, South, Central, North-East).

34. Security_Type :
Indicates direct or indirect security associated with the loan. ['direct' 'Indriect']

35. Status (Target Variable) :
Represents whether the borrower defaulted:
•	1 = Default
•	0 = Not Default

36. dtir1 (Debt-to-Income Ratio) :
Measures applicant’s ability to manage monthly payments. (numeric values)s



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
