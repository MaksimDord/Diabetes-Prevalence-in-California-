# Diabetes-Prevalence-in-California-

## Table of Contents
- [Problem](#Problem)
- [Dataset Source](#Datasaet Source)
- [Research Questions](#Research Questions)
- [Planned Approach](#Planned Approach)

## Problem
The aim of the project is to help the professional medical community of California, research departments, and the state authorities in the field of public health to identify specific health disparities across categories such as race/ethnicity, income, age, education. By analyzing these disparities related to the prevalence of diabeties among Californians, I can help the health authorities to identify specific risk factors correlating with the spread of diabetes.

## Dataset Source
Dataset Title - Adults with Diabetes Per 100 - LGHC (Let's Get Healthy California) Indicator
Data Owner - HHS Office of the Chief Data Officer
Data Provided By - chhs.data.ca.gov
Dataset Source Link - https://healthdata.gov/State/Adults-with-Diabetes-Per-100-LGHC-Indicator-/td3j-8dxk/about_data

## Research Questions

### Question 1 
How has the diabetes prevalence in California changed from 2012 to 2018, and which demographic/socioeconomic variables (Age, Income, Education, Race-Ethnicity, Sex) consistently show the highest prevalence rate of diabetes?
### Question 2
How can parametric regression models (Linear Regression and Ridge Regression)  forecast future diabetes prevalence based on the socio-economic variables such as the household income and educational level for the time period from 2019 to 2029?
### Question 3
What is the maximum difference in the diabetes prevalence in each demographic/socioeconomic variables and which specific variable shows the highest difference in prevalence?

## Planned Approach - End-to-end Data Analytics Pipeline Design

### Step 1 - Data Ingestion and Data Verification 
- Libraries: pandas
- Operation - Load the raw data from the Excel file - Adults with Diabetes Per 100.
- Verification: verify all data across 8 columns, check the dimensions of the loaded data, confirm the absence of missing values and zero null for the complete data verification.

### Step 2 - Initial Data Analysis 
- Libraries: pandas, matplotlib, seaborn
- Operation - Conduct univariate statistics analysis and calculate bivariate disparity.
- Dependency: Proper data ingestion and data verification are required in Step 1.

### Step 3 - Engineering of Specific Features & Preparation of Data Matrix
- Libraries: scikit-learn (sklearn.preprocessing & sklearn.compose)
- Operation - Transform categorical variables ( Strata and Strata Name) into quantitative indicator matrices by applying the One Hot Encoding (Dummy Variable Generation). To normalize these numerical variables for penalty weighting to be assigned equally, StandardScaler should be applied. 
- OneHotEncoder: Converts qualitative categorical attributes (Strata, Strata Name) into numerical binary variables.
- StandardScaler: Normalizes numerical features.
- ColumnTransformer: Connects preprocessing steps into an united pipeline structure
- Dependency: Proper data ingestion and data verification are required in Step 1.

### Step 4 - Parametric Modeling and 5-Fold Cross-Validation
- Libraries: scikit-learn (sklearn.linear_model & sklearn.model_selection)
- Operation - Train and evaluate two parametic regresson models - Liner and Ridge on the dataset. Then conduct 5 Fold Cross validation to to optimize the L2 penalty for Ridge regression.
- LinearRegression: Trains the OLS model.
- Ridge: Trains the L2-regularized regression model to control multicollinearity.
- KFold & cross_val_score: Conducts 5-Fold Cross-Validation to optimize the regularization hyperparameter.
- Dependency: Standardized feature matrices are needed from Step 3

### Step 5 - Predictive Forecasting (2019–2029)
- Libraries: numpy, scikit-learn (sklearn.metrics)
- Operations: Generate the future projections of diabetes prevalence across the demographic variables until 2029. Verify the model performance by using Mean Squared Error (MSE) and coefficient of determination.
- Mean_squared_error and r2_score: Estimates accuracy of the model
- Dependency: Cross-validated and trained parameters are required from Step 4

### Step 6 – Interpretation of the Results 
- Libraries: seaborn, matplotlib.
- Operation – Generate visual charts reflecting the forecast of the research and translate the output into real-world insights for healthcare professionals.








