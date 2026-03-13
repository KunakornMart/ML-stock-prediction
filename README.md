# Machine Learning Coursework: Housing Price Regression & OBTC Trend Prediction

This repository contains a set of Jupyter notebooks created for machine learning practice and coursework. The work covers two main problem types:

1. **Regression** for predicting housing prices using structured tabular data.
2. **Classification** for predicting short-term price direction of **Osprey Bitcoin Trust (OBTC)** using market features and a **Logistic Regression** model.

Rather than being a single production-ready application, this repo is best understood as a **machine learning notebook portfolio / coursework repository** that demonstrates data preprocessing, feature engineering, model training, and basic strategy backtesting.

---

## Repository Overview

### 1) Housing Price Prediction
**Notebook:** `ML_6610422020_KunakornPruksakorn.ipynb`  
**Dataset:** `Housing.csv`

This notebook builds a **Linear Regression** model to estimate house prices from property attributes.

#### Main workflow
- Load the housing dataset from CSV
- Inspect structure, missing values, and descriptive statistics
- Convert categorical yes/no features into numeric binary values
- Expand `furnishingstatus` into separate indicator columns:
  - `furnished`
  - `semi-furnished`
  - `unfurnished`
- Prepare features `X` and target `y`
- Split the data into **80:20 train/test sets**
- Train a **Linear Regression** model
- Evaluate predictions with standard regression metrics

#### Features used
Examples of the variables used in the model include:
- `area`
- `bedrooms`
- `bathrooms`
- `stories`
- `mainroad`
- `guestroom`
- `basement`
- `airconditioning`
- `parking`
- `prefarea`
- furnishing-related indicator columns

#### Learning focus
This notebook demonstrates:
- tabular data cleaning
- categorical encoding
- feature selection
- regression modeling with scikit-learn
- basic model evaluation for price prediction

---

### 2) OBTC Intraday Direction Prediction
**Notebook:** `ML_As2_6610422020.ipynb`

This notebook collects **1-hour interval market data** from Yahoo Finance and builds a **Logistic Regression** model to classify whether the next OBTC closing price will move **up (+1)** or **down / not higher (-1)**.

#### Data sources
- **OBTC** (Osprey Bitcoin Trust)
- **GBTC** (Grayscale Bitcoin Trust)

#### Main workflow
- Download hourly market data using `yfinance`
- Use OBTC as the primary asset
- Pull GBTC data as an additional related market input
- Create engineered features from price behavior and cross-asset relationship
- Define the target using the next-period close direction
- Split the data into **70:30 train/test sets**
- Train a **Logistic Regression** classifier
- Inspect model coefficients
- Generate trading signals and compare cumulative returns

#### Engineered features
The notebook uses features such as:
- `Open`
- `High`
- `Low`
- `Close`
- `GBTC_Open`
- `GBTC_Close`
- `S_10` (short rolling statistic)
- `Corr` (rolling correlation-style feature)
- `Open-Close`
- `Open-Open`

#### Target definition
The label is created as:
- `1` when the **next close > current close**
- `-1` otherwise

#### Backtesting logic
After training the classifier, the notebook:
- predicts trading signals
- computes **OBTC log returns**
- compares them with a simple **strategy return** series
- also compares against **BTC returns** as an additional benchmark

#### Learning focus
This notebook demonstrates:
- financial data collection with `yfinance`
- feature engineering for time-series classification
- binary classification with Logistic Regression
- signal generation
- simple cumulative return comparison

---

### 3) Experimental / Iteration Notebook
**Notebook:** `Test10.ipynb`

This notebook appears to be a later experimental version of the OBTC/GBTC modeling workflow. It includes:
- resetting the DataFrame index
- datetime reformatting
- aligning OBTC and GBTC rows by timestamp
- candlestick plotting with Plotly
- logistic regression retraining

It is useful as a development notebook, but for a cleaner public portfolio it would be better to either:
- rename it to something more descriptive, or
- remove/archive it once the final notebook is ready.

---

## Tech Stack
- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib / Seaborn**
- **Plotly**
- **scikit-learn**
- **yfinance**
- **Jupyter Notebook / Google Colab**

---

## How to Run

### Option 1: Google Colab
1. Upload the notebooks to Colab or open them directly from GitHub.
2. Install required libraries if needed:
   ```bash
   pip install yfinance pandas numpy scikit-learn seaborn matplotlib plotly
   ```
3. Run cells from top to bottom.

### Option 2: Local Jupyter Environment
1. Clone the repository:
   ```bash
   git clone https://github.com/KunakornMart/ML-stock-prediction.git
   cd ML-stock-prediction
   ```
2. Install dependencies:
   ```bash
   pip install yfinance pandas numpy scikit-learn seaborn matplotlib plotly notebook
   ```
3. Start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. Open the notebook you want to run.

---

## Suggested Repository Structure Improvement

To make this repository look stronger for recruiters or portfolio viewers, consider reorganizing it like this:

```text
ML-stock-prediction/
├── README.md
├── requirements.txt
├── data/
│   └── Housing.csv
├── notebooks/
│   ├── 01_housing_price_regression.ipynb
│   ├── 02_obtc_direction_classification.ipynb
│   └── 03_experimental_backtest.ipynb
└── images/
    └── preview_charts.png
```

### Recommended cleanup
- rename notebooks to human-readable names
- remove duplicate notebook versions
- add `requirements.txt`
- add charts/screenshots to the README
- write short project goals for each notebook
- separate **coursework**, **experiments**, and **final notebook versions**

---

## Best Repository Naming Options

The current name, `ML-stock-prediction`, is **okay but incomplete** because the repository also contains a housing-price regression project.

### Better options if you keep both project types in one repo
- `ml-coursework-notebooks`
- `machine-learning-notebook-portfolio`
- `ml-regression-and-trading-lab`
- `applied-machine-learning-notebooks`

### Better options if you want the repo to focus only on the finance project
- `obtc-price-direction-prediction`
- `obtc-logistic-regression-strategy`
- `intraday-trend-prediction-obtc`
- `ml-trading-signal-notebooks`

### Best practical recommendation
If this repo is meant for **portfolio / job applications**, I would recommend either:

**A. Split into 2 repositories**
- `housing-price-regression`
- `obtc-direction-prediction`

or

**B. Keep one repository but rename it**
- `machine-learning-notebook-portfolio`

This will make the project story much clearer.

---

## Future Improvements
- add a proper experiment summary section
- report evaluation metrics clearly in tables
- add confusion matrix / classification report for the OBTC model
- use a time-series-aware validation method
- standardize features before Logistic Regression
- fix convergence warnings by scaling data and tuning solver/max iterations
- move reusable logic into `.py` files
- add a reproducible environment file

---

## Author
**Kunakorn Pruksakorn**  
Machine Learning / Data / Automation enthusiast building notebook-based experiments in regression, classification, and financial modeling.
