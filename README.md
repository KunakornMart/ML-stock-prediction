# OBTC Direction Prediction with Machine Learning

A machine learning project for predicting short-term price direction of **Osprey Bitcoin Trust (OBTC)** using intraday market data, feature engineering, and a Logistic Regression-based trading signal model.

This project focuses on building an end-to-end financial machine learning workflow, from market data collection to model training, signal generation, and simple strategy backtesting.

---

## Project Overview

Financial markets are noisy, fast-moving, and difficult to predict with simple rules.  
This project explores whether short-term OBTC price movement can be modeled using historical price behavior and related market information from GBTC.

The goal is not to build a guaranteed trading system, but to demonstrate a practical machine learning workflow for financial time-series classification.

---

## Key Features

- Collects intraday market data using Yahoo Finance
- Uses OBTC as the main prediction target
- Uses GBTC as an additional related-market feature
- Performs feature engineering on OHLC price data
- Builds a binary classification model for price direction
- Generates model-based trading signals
- Compares cumulative market return vs strategy return
- Visualizes price movement and model-driven performance

---

## Problem Statement

The model predicts whether the next-period OBTC closing price will move upward or not.

Target label:

```text
1  = next close price is higher than current close price
-1 = next close price is lower than or equal to current close price
