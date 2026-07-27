# House Prediction Analysis  

## Overview
This project analyzes the **Boston Housing dataset** to explore the factors that influence
median house prices, using data cleaning, exploratory data analysis, regression,
clustering, classification, and interactive dashboarding.

## Dataset
- House Prediction Data Set
- **Rows:** 506
- **Columns:** CRIM, ZN, INDUS, CHAS, NOX, RM, AGE, DIS, RAD, TAX, PTRATIO, B, LSTAT, MEDV

##  Tasks Completed

### Level 1 — Task 1: Data Cleaning and Preprocessing
- Imported pandas and numpy.
- Loaded the raw dataset — since the file had no header row and was whitespace-separated
   (not comma-separated), supplied the 14 column names manually and used `sep=r'\s+'`
   instead of the default comma delimiter.
- Inspected the data: checked shape (506 rows, 14 columns), data types, and summary
   statistics with `.describe()`.
- Checked every column for missing values using `.isnull().sum()` — printed the count
   before handling. None were found in this dataset, so no imputation was needed (the code
   still includes median-fill logic so it generalizes to a genuinely messy dataset).
 - Checked for duplicate rows using `.duplicated().sum()` and removed any found with
   `.drop_duplicates()` — printed row count before and after (none were found).
- Standardized `CHAS` — it was stored as raw integers (0/1) but is really a categorical
   flag, so it was converted to a labeled `category` dtype (`0 → 'No'`, `1 → 'Yes'`).
- Saved the cleaned dataset as `house_data_cleaned.csv`.

### Level 1 — Task 2: Exploratory Data Analysis (EDA)
- Calculated summary statistics — mean, median, mode, and standard deviation — for every
   numeric column.
- Plotted histograms for all 14 features to see distribution shape (skew, spread).
- Plotted boxplots for all features to detect outliers.
- Created scatter plots of `RM`, `LSTAT`, and `PTRATIO` against `MEDV` to visually check
   relationships with house price.
- Built a correlation matrix and visualized it as a heatmap.
- Extracted and sorted the correlations of every feature against `MEDV` specifically to
   identify the strongest predictors.

### Level 2 — Task 1: Regression Analysis
- Converted `CHAS` back to numeric (0/1) for modeling.
- Selected `RM` (rooms per dwelling) as the predictor and `MEDV` as the target, based on
   it having the strongest correlation from the EDA.
- Split the data into training (80%) and testing (20%) sets using `train_test_split`.
- Fit a `LinearRegression` model on the training data.
- Generated predictions on the test set.
- Interpreted the coefficient — each additional room adds roughly $9,348 to predicted
   median home value.
- Evaluated the model using R-squared (≈0.37) and Mean Squared Error (≈46.14).

### Level 2 — Task 3: Clustering Analysis (K-Means)
- Dropped `MEDV` from the feature set (clustering was done on the predictors only, not
   the target).
- Standardized all features using `StandardScaler`.
- Ran K-Means for k = 1 through 10 and recorded the inertia for each, to apply the elbow method
- Plotted inertia vs. k and identified the elbow bend around **k = 3**.
- Fit the final K-Means model with 3 clusters and assigned each row a cluster label.
- Visualized the clusters with a 2D scatter plot of `RM` vs `MEDV`, colored by cluster.
- Checked average feature values per cluster to interpret what distinguished each group.

### Level 3 — Task 1: Predictive Modeling (Classification)
- Since `MEDV` is continuous, created a categorical target by binning it into three price
   tiers — Low, Medium, High — using `pd.qcut` (tertiles), resulting in a near-even split
   (169/171/166).
- Split features (`X`) and the new target (`y`), then did an 80/20 train-test split with tratification to keep class balance.
- Scaled the features using `StandardScaler`.
- Trained three classification models: Logistic Regression, Decision Tree, and RandomForest.
- Evaluated each model on the test set using accuracy, precision, recall, and F1-score (weighted average), plus a full classification report.
- Ran `GridSearchCV` on Random Forest to tune `n_estimators`, `max_depth`, and `min_samples_split` across 5-fold cross-validation.
- Compared the tuned model's test accuracy against the baseline models.
- Summarized all model results side by side in a comparison table.
  
  ### Level 3 — Task 2: Building a Dashboard with Power BI
- Imported `house_data_cleaned.csv` into Power BI Desktop
- Verified data types for each column in Power Query (numeric fields as Decimal/Whole
   Number).
- Built a bar chart showing average `MEDV` by `CHAS` (river-adjacent vs. not).
- Built a scatter plot of `RM` vs `MEDV` — added an Index column (via **Add Column → Index Column** in Power Query) and set it, along with `RM` and `MEDV`, to "Don'tsummarize" so each of the 506 houses plots as its own point instead of collapsing into one aggregated dot.
- Built a line chart of average `MEDV` by `RM` as a secondary trend view.
- Built a treemap of `RAD` (highway access index) sized by average `MEDV`, used in place
   of a geographic map since the dataset has no location fields.
- Added card visuals for average/min/max `MEDV`.
- Added slicers for `CHAS` and `PTRATIO` to enable interactive filtering across all
   visuals.

## Tools Used
- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Power BI Desktop**

## Key Insights
- `RM` (rooms per dwelling) has the strongest **positive** correlation with house price.
- `LSTAT` (% lower status population) has the strongest **negative** correlation with price.
- K-Means clustering identified 3 distinct neighborhood groups based on socioeconomic
  and structural features.
- A Random Forest classifier best distinguished Low/Medium/High price tiers after
  hyperparameter tuning.

## Files in this repository
- 'House  Prediction Analysis.ipynb'- Jupyter Notebook with all analysis code
- 'House Prediction.pbix'- Power BI interactive dashboard
- 'house_data_cleaned.csv'- Cleaned version of dataset
