# Stock Prices Data Analytics Project

## Overview
A complete data analytics workflow built on a historical stock prices dataset (2014–2017, 497K+ rows, 500+ symbols).

## Dataset

- Stock Prices Data Set
- **Size:** 497,472 rows, 7 columns
- **Columns:** `symbol`, `date`, `open`, `high`, `low`, `close`, `volume`
- **Date range:** 2014-01-02 to 2017-12-29
- **Unique stock symbols:** 505

## Tasks Completed

### Level 1

**Task 1 — Data Cleaning and Preprocessing**
- Identified and removed rows with missing `open`/`high`/`low` values (<0.01% of data)
- Checked for and confirmed 0 duplicate rows
- Converted the `date` column from text to proper `datetime` format
- Final cleaned dataset: 497,461 rows, 0 missing values, 0 duplicates

**Task 3 — Basic Data Visualization**
- Line chart: closing price trend over time (single stock)
- Bar chart: average closing price comparison across multiple stocks
- Scatter plot: trading volume vs. closing price
- Multi-line chart with legend: closing price comparison across several stocks
- All charts exported as PNG images

### Level 2

**Task 1 — Regression Analysis**
- Built a simple linear regression model to predict closing price from opening price
- Split data into 80% training / 20% testing sets
- Evaluated performance using R² and Mean Squared Error (RMSE)
- Visualized actual vs. predicted values with a regression line

**Task 2 — Time Series Analysis**
- Plotted closing price time series to identify overall trend
- Decomposed the series into trend, seasonality, and residual components (statsmodels, period=252 trading days)
- Applied 30-day and 90-day moving averages to smooth short-term fluctuations

### Level 3

**Task 1 — Predictive Modeling (Classification)**
- Created a binary target variable: whether next-day closing price increases or decreases
- Trained and compared three models: Logistic Regression, Decision Tree, Random Forest
- Evaluated using accuracy, precision, recall, and F1-score
- Performed hyperparameter tuning on Random Forest using GridSearchCV

**Task 2 — Building Dashboards with Power BI**
- Imported the cleaned dataset in Power BI
- Built four interactive visuals: total closing price trend, total trading volume (KPI card), top 10 stocks by average closing price, multi-stock closing price comparison
- Added interactive slicers for stock symbol and date range
- Published dashboard for sharing

## Tools Used
- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels
- **Power BI Desktop**

## Key Takeaways
- Missing values in this dataset were minimal (<0.01%) and safely dropped rather than imputed, since imputing financial price data can be misleading.
- Same-day open and close prices are strongly correlated, giving the regression model a high R².
- Predicting next-day price direction from same-day prices alone is genuinely difficult — near-random accuracy reflects the well-known unpredictability of short-term stock movements, not a modeling failure.
- Stock closing prices show a clear long-term upward trend across 2014–2017 with no strong recurring seasonality, typical of financial time series.

## Files in this Repository 
- 'Stock Price.pbix'- Power BI interactive dashboard
- 'Stock Prices Analysis.ipynb'- Jupyter Notebook with all analysis code
- 'Stock_Prices_Cleaned.csv'- Cleaned version of the datset
