# Telecom Customer Churn Analysis Bigml 80

## Dataset
- churn-bigml-80
**Rows:** 2,666
**Columns:**  State, Account length, Area code, International plan, Voice mail plan,  Number vmail messages, Total day minutes, Total day calls, Total day charge, Total eve minutes, Total eve calls, Total eve charge, Total night minutes, Total night calls, Total night charge, Total intl minutes, Total intl calls,  Total intl charge, Customer service calls, Churn,

## Tools Used
**Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels)
Power BI.

## Step-by-Step Task Breakdown

### Level 1 — Basic

**Task 1: Data Cleaning and Preprocessing**
1. Loaded the raw CSV into a pandas DataFrame.
2. Checked shape, data types, missing values per column, and duplicate rows.
3. Handled missing values (none found; imputation logic included for reusability).
4. Removed duplicate rows.
5. Stripped whitespace and standardized casing on categorical columns (`International plan`, `Voice mail plan`).
6. Converted `Churn` to a proper boolean type.
7. Verified the cleaning with an after-cleaning check and saved the result as `churn_cleaned.csv`.

**Task 2: Exploratory Data Analysis (EDA)**
1. Loaded the cleaned dataset.
2. Calculated summary statistics (mean, median, mode, standard deviation) for numerical columns.
3. Checked the class balance of `Churn`.
4. Plotted histograms for key numeric features to view distributions.
5. Plotted boxplots of each feature split by `Churn` to spot early separation between classes.
6. Built a scatter plot of `Total day minutes` vs `Total day charge`, colored by churn.
7. Computed a full correlation matrix and visualized it as a heatmap.
8. Extracted and reviewed the top correlated feature pairs.

### Level 2 — Intermediate

**Task 1: Regression Analysis**
1. Selected `Total day minutes` as the predictor and `Total day charge` as the target.
2. Split the data into training (80%) and test (20%) sets.
3. Fit a linear regression model on the training set.
4. Extracted and interpreted the intercept and coefficient.
5. Predicted on the test set and evaluated with R-squared and mean squared error.
6. Plotted the fitted regression line against actual test data.
7. Plotted residuals to check for patterns in prediction error.

**Task 2: Time Series Analysis**
1. Noted the dataset has no real date/time column.
2. Built a synthetic date index by sorting rows by `Account length` and assigning consecutive daily dates.
3. Plotted the raw synthetic series of `Total day minutes` over time.
4. Decomposed the series into trend, seasonality, and residual components using `statsmodels`.
5. Applied 7-period and 30-period moving averages and plotted them against the raw series.
6. Flagged that
