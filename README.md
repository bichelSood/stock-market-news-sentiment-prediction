# Stock Market Movement Prediction Using News Sentiment Analysis

## Project Overview

This project analyzes the relationship between financial news sentiment and NIFTY50 stock market movement. The goal is to explore whether daily financial news headlines can provide useful signals for predicting whether the market moves up or down.

The project combines financial news headlines with NIFTY50 stock market data. The news data is cleaned, grouped by date, scored using sentiment analysis, and merged with stock price data. After feature engineering and exploratory data analysis, machine learning models are trained to predict daily market movement.

## Problem Statement

Stock market movement is influenced by many factors, including investor sentiment, financial news, economic events, and market behavior. This project focuses on one specific question:

**Can financial news sentiment help predict short-term NIFTY50 market movement?**

## Objectives

- Clean and preprocess financial news and NIFTY50 stock market datasets
- Handle encoding issues and inconsistent date formats
- Group multiple news headlines by trading date
- Merge financial news data with NIFTY50 data
- Generate sentiment scores from daily news headlines using VADER
- Create features such as daily return, volatility, news count, and previous-day sentiment
- Perform exploratory data analysis using visualizations
- Train machine learning models to predict market movement
- Compare model performance and analyze feature importance

## Dataset Description

This project uses two datasets:

### 1. Financial News Dataset

The financial news dataset contains news headlines with publication dates. Multiple headlines may be available for the same date.

Main columns used:

- `Date`
- `Title`

### 2. NIFTY50 Stock Dataset

The stock dataset contains daily NIFTY50 market information.

Main columns used:

- `date`
- `open`
- `high`
- `low`
- `close`
- `shares_traded`
- `turnover_cr`

After cleaning and merging both datasets, the final dataset contains **132 matched trading days**.

## Project Structure

```text
stock-market-news-sentiment-prediction/
│
├── data/
│   ├── news.csv
│   ├── nifty50.csv
│   ├── final_merged_features.csv
│   ├── model_results.csv
│   └── feature_importance.csv
│
├── notebooks/
│   └── 01_analysis.ipynb
│
├── plots/
│   ├── sentiment_label_distribution.png
│   ├── market_movement_distribution.png
│   ├── sentiment_score_over_time.png
│   ├── daily_return_over_time.png
│   ├── sentiment_vs_daily_return.png
│   ├── correlation_heatmap.png
│   ├── random_forest_feature_importance.png
│   └── model_accuracy_comparison.png
│
└── README.md


Raw Financial News Dataset + Raw NIFTY50 Dataset
                    ↓
              Data Cleaning
                    ↓
          Date Format Standardization
                    ↓
          Grouping News by Date
                    ↓
             Dataset Merging
                    ↓
          Sentiment Score Generation
                    ↓
            Feature Engineering
                    ↓
       Exploratory Data Analysis
                    ↓
        Machine Learning Models
                    ↓
        Performance Evaluation


Data Cleaning

During preprocessing, the following cleaning steps were performed:
Fixed messy column names caused by encoding issues
Renamed stock dataset columns manually
Converted date columns into proper datetime format
Converted numerical columns into correct data types
Grouped multiple news headlines by date
Merged news and stock datasets using matching dates


Feature Engineering

The following features were created:
Feature	Description
daily_return	Percentage change from opening price to closing price
movement	Target variable: 1 if market moved up, 0 if market moved down or stayed flat
volatility_pct	Intraday volatility percentage based on high and low prices
sentiment_score	VADER compound sentiment score for daily news headlines
sentiment_label	Sentiment category: positive, negative, or neutral
news_count	Number of news headlines available for a trading day
prev_day_sentiment	Previous trading day's sentiment score


Exploratory Data Analysis

The EDA section includes the following visualizations:
Sentiment label distribution
Market movement distribution
Sentiment score over time
Daily market return over time
Sentiment score vs daily return
Correlation heatmap
Random Forest feature importance
Model accuracy comparison
Key observations:
The market movement classes were almost balanced.
There were 67 down/flat days and 65 up days.
VADER classified most daily news sentiment as positive.
Sentiment score did not show a strong direct linear relationship with daily return.
Random Forest performed slightly better than Logistic Regression.


Machine Learning Models

The target variable for prediction was:
movement
Where:
0 = market moved down or stayed flat
1 = market moved up
The following features were used for model training:
sentiment_score
prev_day_sentiment
news_count
volatility_pct
Two machine learning models were trained:
Logistic Regression
Random Forest Classifier


Model Results

Model	                    Accuracy 
Logistic Regression	        51.85%
Random Forest Classifier	  55.56%
Random Forest gave slightly better accuracy than Logistic Regression.


Feature Importance

The Random Forest model gave the following feature importance values:
Feature	              Importance
volatility_pct	       0.273635
sentiment_score	       0.262380
prev_day_sentiment	   0.259320
news_count	           0.204665


This shows that all selected features contributed to the prediction, with volatility_pct having the highest importance.


Limitations

The final merged dataset contains only 132 trading days, which is small for machine learning.
VADER is a general-purpose sentiment analyzer and may not fully understand financial context.
Most sentiment scores were classified as positive, which may reduce the usefulness of sentiment labels.
Stock markets are affected by many external factors beyond news headlines.
Same-day volatility may not be available before market close in a real-time prediction scenario.


Conclusion

This project demonstrates an end-to-end data analysis and machine learning workflow using financial news sentiment and NIFTY50 market data. The results show that sentiment-based features may provide some useful signals, but they are not enough on their own to predict market movement with high accuracy.
The project highlights the importance of data cleaning, feature engineering, visualization, model comparison, and honest evaluation when working with real-world financial data.


