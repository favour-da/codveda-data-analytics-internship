# Codveda Data Analytics Internship — Customer Churn Analysis

## About the Project
A customer-level dataset from a telecom provider, used to analyze and predict churn   

## Dataset
- churn-bigml-20
- **Rows:** 667 customer records
- **Columns:** `State`, `Account length`, `Area code`, `International plan`, `Voice mail plan`, `Number vmail messages`, `Total day minutes / calls / charge`,`Total eve minutes / calls / charge`, `Total night minutes / calls / charge`, `Total intl minutes / calls / charge`, `Customer service calls`, `Churn`.

### Task Completed 

## Level 1
### Task 1: Data Cleaning and Preprocessing
- Loaded the dataset with pandas
- Verified no missing values or duplicates present
- Standardized categorical text formatting (stripped whitespace, consistent casing)
- Converted `International plan`, `Voice mail plan`, and `Churn` to binary (1/0)
- Cleaned column names to lowercase with underscores
- Exported cleaned dataset as `churn_cleaned.csv`

### Task 3: Basic Data Visualization
- Bar plot: churn distribution (stayed vs. churned)
- Line chart: average daytime minutes vs. customer service calls
- Scatter plot: total day minutes vs. total day charge, colored by churn status
- All plots exported as PNG images

## Level 2

### Task 1: Regression Analysis
- Built a simple linear regression model predicting `total_day_charge` from `total_day_minutes`
- Split data into training (80%) and testing (20%) sets
- Evaluated using R-squared and Mean Squared Error
- Model achieved a near-perfect fit (R² close to 1.0), reflecting the proportional billing relationship in the data
- Visualized the regression line against actual test data


### Task 3: Clustering Analysis (K-Means)
- Standardized numeric features using `StandardScaler`
- Applied K-Means clustering with the elbow method to determine optimal `k`
- Segmented customers into `k=3` clusters based on usage patterns
- Visualized clusters using a 2D scatter plot (total day minutes vs. customer service calls)

## Level 3 (Advanced)

### Task 1: Predictive Modeling (Classification)
- Preprocessed data: label-encoded `state`, scaled numeric features
- Trained and compared three models: Logistic Regression, Decision Tree, Random Forest
- Evaluated using Accuracy, Precision, Recall, and F1-score
- Performed hyperparameter tuning on Random Forest using GridSearchCV
- Identified `customer_service_calls` and `international_plan` as top churn predictors via feature importance

### Task 2: Building Dashboards with Power BI
- Imported and cleaned dataset in Power BI
- Built KPI cards: Total Customers, Churned Customers, Churn Rate
- Created interactive visualizations: bar charts (churn by state, churn by international plan), line chart (avg. service calls by churn), scatter chart (day minutes vs. day charge by churn)
- Added slicers for `state`, `international_plan`, and `voice_mail_plan` for interactive filtering

## Key Insights 
- Customers who churned made noticeably more support calls on average than those who stayed — frustration with support appears to be a leading churn driver.
- Customers on an international plan churn disproportionately more than those without one, suggesting pricing or service issues specific to that plan.
- Regression confirmed an almost exact 1:1 relationship (R² near 1.0), consistent with per-minute billing — this variable pair isn't independently predictive of churn beyond that.
- K-Means (k=3) revealed groups based on usage intensity (light, moderate, heavy users), useful for targeted retention strategies rather than treating all customers the same.
- Some states show notably higher churn rates than others, which could point to regional service quality or competitive pressure worth investigating further.
- With `customer_service_calls` and `international_plan` ranking as the top predictive features — reinforcing the two insights above with a data-driven feature importance ranking.
 
## Tools Used
- **Python** — pandas, numpy, matplotlib, seaborn, scikit-learn (LinearRegression, KMeans, StandardScaler, LogisticRegression, DecisionTreeClassifier, RandomForestClassifier, GridSearchCV)
- **Power BI**

## Files in this repository 
- 'Churn-bigml-20.pbix'- Power BI interactive dashboard
- 'churn-bigml-20 analysis.ipynb'- Jupyter notebook with all analysis code
- 'cvhurn-bigml-20_cleaned.csv'- Cleeaned version of datset 
