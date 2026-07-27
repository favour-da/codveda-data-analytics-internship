# Sentiment Dataset Analysis

## Overview
This project applies to a social media sentiment dataset, containing posts with engagement metrics (likes, retweets), platform, country, timestamp, and fine-grained emotion labels (279 unique sentiment categories, e.g. Joy, Excitement, Neutral, Adrenaline).

## Dataset 
- Sentiment Dataset
- **Rows**: 732
- **Columns**: Unnamed: 0.1, Unnamed: 0, Text, Sentiment, Timestamp, User, Platform, Hashtags, Retweets, Likes, Country, Year, Month, Day, Hour

## Tools Used
- **Python:** pandas, numpy matplotlib, seaborn, wordcloud scikit-learn (StandardScaler, KMeans, LogisticRegression, DecisionTreeClassifier, RandomForestClassifier, GridSearchCV), statsmodels (seasonal_decompose), nltk, TextBlob

## Tasks Completed

### Level 1 (Basic)
**Task 1 — Data Cleaning and Preprocessing**
- Loaded raw CSV with pandas
- Dropped stray unnamed index columns
- Stripped whitespace from all text/categorical columns
- Handled missing values (dropped rows missing `Text`/`Sentiment`; filled missing engagement counts with 0)
- Removed duplicate rows
- Standardized formats: converted `Timestamp` to datetime, title-cased categorical fields, cast engagement counts to integers
- Output: `sentiment_dataset_cleaned.csv`

**Task 2 — Exploratory Data Analysis (EDA)**
- Summary statistics (mean, median, mode, std) for Retweets and Likes
- Distribution visualizations: histograms, boxplots
- Boxplot of Likes by Sentiment
- Scatter plot of Retweets vs Likes
- Correlation heatmap between numeric features
- Bonus: sentiment trend over time (daily post counts by sentiment category)

### Level 2 
**Task 2 — Time Series Analysis**
- Built a daily time series of post count, total likes, and total retweets
- Plotted time-series trends
- Applied 3-day and 7-day moving average smoothing
- Seasonal decomposition (trend, seasonality, residuals) using `statsmodels`

**Task 3 — Clustering Analysis (K-Means)**
- Standardized engagement features (Retweets, Likes) with `StandardScaler`
- Determined optimal cluster count via the elbow method
- Applied K-Means clustering and visualized clusters with a 2D scatter plot
- Compared cluster engagement averages and cross-tabulated clusters against sentiment labels
  
### Level 3
**Task 1 — Predictive Modeling (Classification)**
- Since the raw dataset contains 279 fine-grained emotion labels (many with only 1 sample), labels were grouped into broad **Positive / Negative / Neutral** categories using TextBlob polarity scoring of each emotion word
- Engineered features: Retweets, Likes, Platform, Country, Hour, Day of Week (one-hot encoded / scaled)
- Trained and compared Logistic Regression, Decision Tree, and Random Forest classifiers
- Evaluated with accuracy, precision, recall, F1-score
- Tuned Random Forest hyperparameters via `GridSearchCV`
- **Finding:** engagement/platform/time metadata are weak predictors of sentiment on their own — a realistic and expected limitation, since sentiment is primarily carried by the text itself

**Task 3 — NLP: Sentiment Analysis**
- Preprocessed post text: lowercased, removed URLs/mentions/punctuation, tokenized, removed stopwords, lemmatized
- Applied TextBlob polarity scoring to classify each post as Positive / Negative / Neutral
- Compared TextBlob predictions against the broad ground-truth sentiment labels
- Visualized predicted sentiment distribution
- Generated word clouds per sentiment class and an overall top-20 word frequency chart
  
## Limitations / Notes
- The dataset's 279 fine-grained emotion labels made direct multi-class classification impractical; broad grouping into 3 classes was used instead.
- TextBlob's lexicon-based sentiment scoring is a simple rule-based approach and does not fully capture the nuance of the original fine-grained emotion labels — accuracy against ground truth reflects this gap.
- Time series decomposition assumes a weekly (7-day) seasonal cycle; adjust `period` if a different cadence is more appropriate for future analysis.

## Files in this repository
- 'Sentiment Analysis.ipynb'- Jupyter notebook containing all analysis code
- 'sentiment_dataset_cleaned.csv'- Cleaned version of the datset
