# Customer Churn Prediction Using Machine Learning

## Project Overview

This project aims to predict customer churn using machine learning models. Customer churn refers to the situation where customers stop using a company's service. Predicting churn can help companies identify high-risk customers earlier and develop customer retention strategies.

The dataset used in this project is the Telco Customer Churn dataset. Each row represents one customer, and the target variable is `Churn`, which indicates whether the customer has left the company.

This project demonstrates a complete machine learning workflow, including data cleaning, exploratory data analysis, feature preprocessing, model training, model evaluation, cross-validation, hyperparameter tuning, feature importance analysis, and model saving.

---

## How to Run

Open `notebook/churn_prediction.ipynb` in Jupyter Notebook or VS Code and run the cells from top to bottom. The dataset is stored in `data/customer_churn.csv`.

---

## Project Structure

- `data/` contains the customer churn dataset.
- `notebook/` contains the full machine learning workflow.
- `model/` contains the saved model, scaler, and feature column list.
- `README.md` summarizes the project and results.

---

## Key Skills Demonstrated

- Data cleaning and missing value handling
- Exploratory data analysis
- Categorical feature encoding
- Model training and comparison
- Cross-validation and hyperparameter tuning
- Feature importance analysis
- Model saving with Joblib

---

## Dataset

The dataset contains customer demographic information, service usage information, contract details, payment methods, and customer charges.

Main features include:

- `gender`
- `SeniorCitizen`
- `Partner`
- `Dependents`
- `tenure`
- `PhoneService`
- `InternetService`
- `Contract`
- `PaymentMethod`
- `MonthlyCharges`
- `TotalCharges`
- `Churn`

The original dataset contained 7,043 records and 21 columns. After data cleaning, 7,032 records were used for model training and evaluation.

---

## Project Workflow

The main steps of this project include:

1. Data loading
2. Data understanding
3. Data cleaning
4. Exploratory data analysis
5. Feature preprocessing
6. Train-test split
7. Model training
8. Model evaluation
9. Model comparison
10. Cross-validation
11. Hyperparameter tuning
12. Feature importance analysis
13. Model saving

---

## Data Cleaning

The `TotalCharges` column was originally stored as an object type, although it represents numerical values. Therefore, it was converted into numeric format using `pd.to_numeric()`.

After conversion, 11 missing values were identified. Since the number of missing records was very small compared with the whole dataset, these rows were removed.

After removing missing values, the dataset was reduced from 7,043 records to 7,032 records.

---

## Exploratory Data Analysis

Exploratory data analysis was conducted to understand customer churn distribution and the relationship between important features and churn.

The analysis focused on:

- Distribution of churned and non-churned customers
- Relationship between contract type and churn
- Relationship between internet service type and churn
- Relationship between monthly charges and churn

The analysis showed that customer contract type, service usage, and charging behavior were closely related to churn patterns.

---

## Feature Preprocessing

Before model training, categorical variables were converted into numerical format using one-hot encoding.

The target variable `Churn` was also encoded into binary values:

- `Yes` = 1
- `No` = 0

The dataset was then split into training and testing sets using an 80:20 ratio.

---

## Models Used

Three machine learning models were trained and compared:

- Logistic Regression
- Decision Tree
- Random Forest

Logistic Regression was trained using standardized features, while tree-based models were trained using the original encoded features.

---

## Model Performance

The models were first evaluated using a train-test split.

| Model | Test Accuracy |
|---|---:|
| Logistic Regression | 0.8038 |
| Decision Tree | 0.7185 |
| Random Forest | 0.7875 |
| Tuned Random Forest | 0.7903 |

Logistic Regression achieved the highest test accuracy among the models.

---

## Cross-Validation

5-fold cross-validation was used to evaluate model stability.

| Model | CV Mean Accuracy |
|---|---:|
| Logistic Regression | 0.8025 |
| Random Forest | 0.7856 |

The cross-validation results were consistent with the train-test split results. Logistic Regression still showed the best overall performance.

---

## Hyperparameter Tuning

GridSearchCV was used to tune the hyperparameters of the Random Forest model.

The best parameters found were:

```python
{
    "max_depth": 10,
    "min_samples_split": 2,
    "n_estimators": 100
}
```

---

## Limitations and Future Improvements

This project is a learning-focused machine learning project, so there are still several areas that can be improved:

- The dataset has class imbalance, so accuracy alone may not fully describe model performance.
- The model comparison is still simple and focuses on a small set of common machine learning models.
- The project currently saves the trained model, but it does not include a deployed prediction application yet.

Future improvements could include:

- Using SMOTE or class weighting to better handle class imbalance.
- Adding ROC-AUC, precision, recall, and F1-score analysis for a more complete evaluation.
- Trying more advanced models such as XGBoost.
- Building a simple prediction app using Streamlit or Flask.
