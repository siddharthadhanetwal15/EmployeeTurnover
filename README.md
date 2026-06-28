## Project Overview: Employee Attrition Prediction

This project aims to analyze employee data to understand the factors contributing to employee attrition and to build a predictive model to identify employees at risk of leaving the company.

### Key Steps:

1.  **Data Loading and Initial Exploration:**
    *   Loaded the `HR_comma_sep.csv` dataset.
    *   Performed initial data inspections using `.head()`, `.shape()`, `.info()`, and `.describe()`.
    *   Checked for missing values (`.isna().sum()`) and duplicate entries.

2.  **Data Preprocessing:**
    *   Removed duplicate rows from the dataset.
    *   Renamed the 'sales' column to 'department' for clarity.
    *   Grouped 'support' and 'IT' departments into a single 'technical' category.
    *   Applied `LabelEncoder` to convert categorical features (`department`, `salary`) into numerical representations.

3.  **Exploratory Data Analysis (EDA):**
    *   Filtered the dataset to analyze employees who have left the company (`df_left`).
    *   Visualized relationships between `last_evaluation`, `satisfaction_level`, `number_project`, `average_montly_hours`, `time_spend_company`, and `department` for employees who left using scatter plots and count plots.
    *   **Key Findings from EDA:** Identified two major factors for employees leaving the organization:
        *   **Work overload:** Employees assigned too many projects (e.g., 3-4 projects) and those with high average monthly hours were more likely to leave.
        *   **Low/Medium Salary:** A significant number of employees who left had low or medium salaries.

4.  **Outlier Detection:**
    *   Used box plots (`plotly.express.box`) to visually inspect potential outliers in numerical features like `satisfaction_level`, `last_evaluation`, `number_project`, `time_spend_company`, and `average_montly_hours`.

5.  **Handling Data Imbalance (SMOTE):**
    *   Observed a class imbalance in the target variable ('left').
    *   Applied the **SMOTE (Synthetic Minority Over-sampling Technique)** algorithm to balance the classes in the dataset, ensuring fair model training.

6.  **Model Training and Evaluation:**
    *   Split the data into training and testing sets.
    *   Trained and evaluated several classification models:
        *   **Logistic Regression:** Achieved a cross-validation score of approximately 80%.
        *   **Decision Tree Classifier:** Showed strong performance with a cross-validation score of around 95%.
        *   **Random Forest Classifier:** Hyperparameter tuning using `GridSearchCV` identified optimal parameters (`criterion='gini'`, `n_estimators=15`) leading to a high cross-validation score of 97%.
        *   **K-Nearest Neighbors (KNN):** Evaluated different `n_neighbors` values; a `n_neighbors=6` resulted in a cross-validation score of 94%.

### Conclusion:

Based on the analysis, **Random Forest Classifier** emerged as the best-performing model for predicting employee attrition with a high accuracy of 97%. The primary reasons identified for employees leaving the company were **work overload** and **low/medium salaries**.
