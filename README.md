# Bitcoin Price Direction Prediction ₿

This project uses machine learning to predict whether the price of Bitcoin will go up or down on the following day. Instead of forecasting the exact price, this model is framed as a **binary classification problem**, predicting a "buy" (price up) or "don't buy" (price down/same) signal.

## 📈 Project Overview

The core objective is to analyze historical Bitcoin OHLC (Open, High, Low, Close) data to build a predictive model. The process involves data cleaning, exploratory data analysis (EDA), feature engineering, and training several classification models to identify the most reliable one for predicting the next day's price movement. The final model chosen is **Logistic Regression**, which provides a slight predictive edge over a random guess.

-----

## 🛠️ Methodology

1.  **Data Loading and Cleaning:**

      * The historical Bitcoin price data from 2014 to 2022 is loaded from a CSV file.
      * Initial data inspection is performed to check for redundant columns (like `Adj Close`) and missing values.

2.  **Exploratory Data Analysis (EDA):**

      * Visualizations such as line charts, distribution plots, and box plots are used to understand the price trends, data distribution, and identify outliers over the years.

3.  **Feature Engineering:**

      * New time-based features (`year`, `month`, `day`, `is_quarter_end`) are created from the `Date` column to capture temporal patterns.
      * Features to represent daily volatility (`open-close`, `low-high`) are engineered.
      * A **`target` variable** is created to define the classification task:
          * `1`: If the next day's closing price is higher than the current day's.
          * `0`: If the next day's closing price is lower or the same.

4.  **Data Preprocessing:**

      * The engineered features are scaled using `StandardScaler` to normalize the data, which helps improve model performance.
      * The dataset is split into a 70% training set and a 30% validation set.

5.  **Model Development and Evaluation:**

      * Three different machine learning models are trained: **Logistic Regression**, **Support Vector Classifier (SVC)**, and **XGBoost Classifier**.
      * Models are evaluated using the **ROC AUC score** on both training and validation sets to check for performance and overfitting.
      * The **Logistic Regression** model was selected as the most balanced, and its performance was further analyzed using a confusion matrix.

-----

## 🚀 Results

  * The **Logistic Regression** model achieved a validation accuracy (ROC AUC) of **51.2%**, indicating it performs slightly better than chance.
  * The **XGBoost Classifier** showed a high training accuracy (94.2%) but a low validation accuracy (46.7%), indicating significant overfitting.
  * The pie chart of the `target` variable showed a fairly balanced dataset, with approximately 53% of days seeing a price increase and 47% seeing a decrease.
