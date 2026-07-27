# Telecom Customer Churn Analysis Bigml 80

## Dataset
- churn-bigml-80
**Rows:** 2,666
**Columns:**  State, Account length, Area code, International plan, Voice mail plan,  Number vmail messages, Total day minutes, Total day calls, Total day charge, Total eve minutes, Total eve calls, Total eve charge, Total night minutes, Total night calls, Total night charge, Total intl minutes, Total intl calls,  Total intl charge, Customer service calls, Churn,

## Tools Used
**Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels)
Power BI.

## Task completed 

### Level 1 

**Task 1: Data Cleaning and Preprocessing**
- Loaded the raw CSV into a pandas DataFrame.
-  Checked shape, data types, missing values per column, and duplicate rows.
-  Handled missing values (none found; imputation logic included for reusability).
- Removed duplicate rows.
- Stripped whitespace and standardized casing on categorical columns (`International plan`, `Voice mail plan`).
- Converted `Churn` to a proper boolean type.
- Verified the cleaning with an after-cleaning check and saved the result as `churn_cleaned.csv`.

**Task 2: Exploratory Data Analysis (EDA)**
- Calculated summary statistics (mean, median, mode, standard deviation) for numerical columns.
- Checked the class balance of `Churn`.
- Plotted histograms for key numeric features to view distributions.
- Plotted boxplots of each feature split by `Churn` to spot early separation between classes.
- Built a scatter plot of `Total day minutes` vs `Total day charge`, colored by churn.
- Computed a full correlation matrix and visualized it as a heatmap.
- Extracted and reviewed the top correlated feature pairs.

### Level 2

**Task 1: Regression Analysis** 
- Selected `Total day minutes` as the predictor and `Total day charge` as the target.
- Split the data into training (80%) and test (20%) sets.
- Fit a linear regression model on the training set.
- Extracted and interpreted the intercept and coefficient.
- Predicted on the test set and evaluated with R-squared and mean squared error.
- Plotted the fitted regression line against actual test data.
- Plotted residuals to check for patterns in prediction error.


**Task 3: Clustering Analysis (K-Means)**
- Selected seven usage-related numeric features for clustering.
- Standardized the features using `StandardScaler`.
- Ran the elbow method (k = 1 to 10) and plotted inertia to identify the optimal number of clusters.
- Fit K-Means with the chosen k (4).
- Reviewed cluster sizes and computed the mean feature profile per cluster.
- Calculated churn rate per cluster to connect clusters to business meaning.
- Visualized clusters on two raw features (day minutes vs service calls).
- Reduced all features to 2D with PCA and visualized cluster separatio
  
### Level 3

**Task 1: Predictive Modeling (Classification)**
- Encoded `International plan` and `Voice mail plan` as binary (0/1).
- One-hot encoded `State` and dropped `Area code`.
- Split data into training/test sets, stratified by `Churn` to preserve class balance.
- Scaled features for Logistic Regression
- Trained Logistic Regression, Decision Tree, and Random Forest models.
- Compared all three models on accuracy, precision, recall, and F1-score.
- Ran GridSearchCV on the Random Forest to tune `n_estimators`, `max_depth`, and `min_samples_split`.
- Evaluated the tuned model on the test set with a full classification report.
- Plotted a confusion matrix for the tuned model.
- Extracted and plotted the top 10 most important features.

**Task 2: Power BI Dashboard** 
- Imported `churn_cleaned.csv` into Power BI and confirmed data types in Power Query
- Created DAX measures: `Total Customers`, `Churned Customers`, `Churn Rate`, `Retained Customers`.
- Built a card visual showing overall `Churn Rate`.
- Built a bar chart of `Churned Customers` by `State`, filtered to the top 10.
- Built clustered column charts of `Churn Rate` by `International plan` and by `Voice mail plan`.
- Built a line chart of `Churn Rate` against `Customer service calls`.
- Built a scatter chart of `Total day minutes` vs `Total day charge`, colored by `Churn`.
- Added slicers for `State`, `International plan`, `Voice mail plan`, and a numeric range slicer for `Customer service calls`.

  ## Key Insights
- Customers with an **international plan** churn at a noticeably higher rate than those without one.
- **Customer service calls** show a strong relationship with churn — churn rate rises sharply once a customer has made more than 3–4 service calls, a useful early-warning signal.
- `Total day/eve/night minutes` and their matching `charge` columns are near-perfectly correlated, since charge is a fixed rate applied to minutes — confirmed visually in both the regression and scatter plot tasks.
- Overall churn rate sits at a minority class (imbalanced dataset), which was accounted for by stratifying the train/test split and using precision/recall/F1 alongside accuracy in model evaluation.
- The Random Forest classifier, after tuning, outperformed Logistic Regression and the single Decision Tree on F1-score,
with day-usage features and customer service calls ranking among the top predictors of churn.

## Files in this Repository 
- 'Churn-bigml-80.pbix'- Power BI interactive dashboard.
- 'churn-bigml-80.ipynb'- Jupyter Notebook with all analysis code
- 'churn-bigml-80_cleaned.csv'- Cleaned version of dataset
