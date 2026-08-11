# NIFTY 50 Financial Time Series Analysis

> Financial time-series analysis of NIFTY 50 returns using Reliance, WTI crude oil, and USD/INR with stationarity testing, OLS regression, diagnostics, and risk analysis.

## About the Project

This project analyzes the relationship between NIFTY 50 returns and selected financial market variables over the period **1 April 2023 to 31 March 2025**.

The analysis focuses on four financial series:

- NIFTY 50
- Reliance Industries
- WTI Crude Oil
- USD/INR Exchange Rate

Daily price data is cleaned, aligned, and transformed into logarithmic returns before conducting statistical and econometric analysis.

The study examines the statistical properties of the financial series, their relationships with each other, and the extent to which Reliance, crude oil, and USD/INR returns explain movements in NIFTY 50 returns.

---

## Research Question

**How do Reliance returns, crude oil returns, and USD/INR returns influence NIFTY 50 returns?**

The analysis also evaluates whether the resulting OLS model satisfies the major assumptions required for reliable statistical inference.

---

## Objectives

The project aims to:

1. Collect and align daily financial market data.
2. Calculate daily logarithmic returns.
3. Test the stationarity of price and return series using the Augmented Dickey-Fuller (ADF) test.
4. Analyze descriptive statistics and risk characteristics.
5. Examine correlations between the financial variables.
6. Estimate an OLS regression model for NIFTY 50 returns.
7. Evaluate coefficient significance and model fit.
8. Conduct regression diagnostic tests.
9. Interpret the results and identify limitations of the OLS model.

---

## Data

The analysis covers the financial period:

**1 April 2023 to 31 March 2025**

The datasets used in the analysis are:

| Dataset | Description |
|---|---|
| NIFTY 50 | Indian benchmark equity index |
| Reliance | Reliance Industries stock prices |
| WTI Crude Oil | Crude oil price data |
| USD/INR | US Dollar to Indian Rupee exchange rate |

The final analysis uses **476 clean observations** after aligning the datasets and calculating returns.

---

## Methodology

The analytical workflow follows these stages:

```text
Raw Financial Data
        |
        v
Data Loading and Cleaning
        |
        v
Date Alignment
        |
        v
Price Series Construction
        |
        v
Log Return Calculation
        |
        v
Stationarity Testing
        |
        v
Descriptive Statistics
        |
        v
Correlation Analysis
        |
        v
OLS Regression
        |
        v
Regression Diagnostics
        |
        v
Risk Analysis
        |
        v
Interpretation
````

---

## Logarithmic Returns

Daily logarithmic returns are calculated to transform price and exchange-rate series into a form suitable for time-series analysis.

The return is calculated as:

```text
r_t = ln(P_t / P_(t-1))
```

where:

* `P_t` is the current price
* `P_(t-1)` is the previous day's price

Using returns allows the analysis to focus on daily changes rather than non-stationary price levels.

---

## Stationarity Analysis

Stationarity is evaluated using the **Augmented Dickey-Fuller (ADF) test**.

The analysis finds that the price-level series are non-stationary, while the corresponding return series are strongly stationary.

All four return series have reported ADF p-values of approximately **0.000000**, leading to rejection of the unit-root null hypothesis.

This supports the use of return series for subsequent econometric modeling.

---

## Descriptive and Risk Analysis

The analysis examines:

* Mean return
* Variance
* Volatility
* Skewness
* Kurtosis
* Maximum drawdown
* Extreme return events
* Rolling volatility
* Risk-adjusted performance

### Selected Findings

| Metric            | NIFTY 50 | Reliance |
| ----------------- | -------: | -------: |
| Annualized Return |   15.96% |        — |
| Volatility        |   12.28% |    54.4% |
| Maximum Drawdown  |        — |    77.8% |
| Kurtosis          |        — |   342.26 |

Reliance exhibits substantially higher volatility and maximum drawdown than NIFTY 50 in the reported analysis.

The distributions also exhibit excess kurtosis, indicating the presence of fat tails and extreme observations.

---

## Correlation Analysis

The analysis examines pairwise correlations between the four return series.

Selected relationships include:

| Relationship     | Correlation |
| ---------------- | ----------: |
| NIFTY - Reliance |       0.228 |
| NIFTY - USD/INR  |      -0.234 |

NIFTY 50 returns show a positive relationship with Reliance returns and a negative relationship with USD/INR returns in the reported sample.

---

## OLS Regression

The following model is estimated:

```text
NIFTY_Returns =
β₀
+ β₁(Reliance_Returns)
+ β₂(Oil_Returns)
+ β₃(USDINR_Returns)
+ ε
```

### Dependent Variable

**NIFTY 50 Returns**

### Independent Variables

* Reliance Returns
* WTI Crude Oil Returns
* USD/INR Returns

---

## Regression Results

| Predictor        | Coefficient |  p-value | Significance    |
| ---------------- | ----------: | -------: | --------------- |
| Reliance Returns |     +0.0500 | 0.000001 | Significant     |
| Oil Returns      |     -0.0128 | 0.483219 | Not significant |
| USD/INR Returns  |     -1.2802 | 0.000000 | Significant     |

The overall regression is statistically significant with:

```text
F-statistic = 18.00
R² ≈ 10.3%
```

The model explains approximately **10.3% of the variation in daily NIFTY 50 returns**, indicating relatively weak explanatory power.

---

## Interpretation

### Reliance Returns

Reliance returns have a positive and statistically significant relationship with NIFTY 50 returns.

The estimated coefficient is:

```text
β = +0.0500
```

with a p-value of:

```text
p = 0.000001
```

The positive relationship is consistent with Reliance's importance within the NIFTY index.

### USD/INR Returns

USD/INR returns have a statistically significant negative relationship with NIFTY returns.

The estimated coefficient is:

```text
β = -1.2802
```

with:

```text
p = 0.000000
```

The analysis indicates that movements associated with Rupee depreciation are negatively related to NIFTY returns.

### Crude Oil Returns

Crude oil returns are not statistically significant in the estimated model.

```text
β = -0.0128
p = 0.483219
```

Therefore, the analysis does not provide sufficient evidence of a linear relationship between daily crude oil returns and NIFTY returns within this model.

---

## Regression Diagnostics

The OLS model is evaluated using several diagnostic tests.

### Durbin-Watson Test

```text
Durbin-Watson = 2.1113
```

The result indicates no substantial evidence of first-order autocorrelation in the residuals.

### Multicollinearity

The reported maximum VIF is approximately:

```text
VIF = 1.024
```

This indicates that multicollinearity is not a major concern among the explanatory variables.

### White Test

```text
p-value = 0.000000
```

The null hypothesis of homoskedasticity is rejected.

The residuals therefore exhibit evidence of **heteroskedasticity**, meaning the variance of the errors is not constant.

### Jarque-Bera Test

```text
p-value = 0.000000
```

The residuals do not follow a normal distribution.

The presence of excess kurtosis and volatility clustering further indicates that the normality assumption is not satisfied.

---

## Key Findings

* All four return series were found to be strongly stationary.
* NIFTY 50 generated an annualized return of approximately 15.96% over the study period.
* Reliance exhibited substantially higher volatility than NIFTY 50.
* NIFTY returns were positively correlated with Reliance returns.
* NIFTY returns were negatively correlated with USD/INR returns.
* Reliance returns were statistically significant in the OLS model.
* USD/INR returns were statistically significant in the OLS model.
* Crude oil returns were not statistically significant.
* The overall OLS model was statistically significant.
* The model's explanatory power was relatively weak, with an R² of approximately 10.3%.
* The model did not satisfy the assumptions of homoskedasticity and normally distributed residuals.

---

## Model Reliability

Although the OLS model identifies statistically significant relationships, its reliability for risk assessment and inference is limited.

The model successfully passes the reported autocorrelation and multicollinearity checks but fails the heteroskedasticity and normality diagnostics.

Therefore, the OLS results should be interpreted as evidence of linear relationships rather than as a complete model of NIFTY 50 return behavior.

The presence of volatility clustering suggests that a volatility model such as **GARCH** could be explored as a next step.

---

## Visualizations

The project includes visual analysis of:

* Price movements
* Return distributions
* Rolling correlations
* Rolling volatility
* Correlation matrix
* Risk metrics
* Maximum drawdown
* Regression coefficients
* Regression residuals
* Q-Q plots
* Leverage and influence
* Residual distributions
* Risk contribution

---

## Repository Structure

```text
nifty-50-financial-time-series-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── raw/
│   │   ├── nifty50_2023.csv
│   │   ├── nifty50_2024.csv
│   │   ├── reliance_2023.csv
│   │   ├── reliance_2024.csv
│   │   ├── crude_oil_wti.csv
│   │   └── usd_inr.csv
│   │
│   └── processed/
│       └── merged_financial_time_series.csv
│
├── notebooks/
│   ├── 01_financial_time_series_analysis.ipynb
│   └── original_submission_notebook.ipynb
│
├── src/
│   └── analysis.py
│
├── results/
│   ├── tables/
│   └── figures/
│
└── docs/
    ├── case_study_report.pdf
    └── case_study_report.docx
```

---

## Tools and Technologies

### Programming

* Python
* Jupyter Notebook

### Libraries

* Pandas
* NumPy
* SciPy
* Statsmodels
* Matplotlib
* Seaborn

### Econometric Techniques

* Logarithmic Returns
* Augmented Dickey-Fuller Test
* Descriptive Statistics
* Correlation Analysis
* Ordinary Least Squares Regression
* Durbin-Watson Test
* Variance Inflation Factor
* White Test
* Jarque-Bera Test
* Volatility and Risk Analysis

---

## Getting Started

Clone the repository:

```bash
git clone https://github.com/<your-username>/nifty-50-financial-time-series-analysis.git
```

Navigate to the project:

```bash
cd nifty-50-financial-time-series-analysis
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
notebooks/01_financial_time_series_analysis.ipynb
```

---

## Dataset Availability

The repository contains the financial datasets used for the analysis.

The raw datasets include:

* NIFTY 50 historical data
* Reliance historical data
* WTI crude oil data
* USD/INR exchange-rate data

The processed dataset contains the aligned observations used for the analysis.

---

## Documentation

The complete academic case study is available under:

```text
docs/case_study_report.pdf
```

The editable report is also included:

```text
docs/case_study_report.docx
```

The original submitted notebook is preserved separately from the cleaned project notebook.

---

## Limitations

* The analysis covers a limited period from April 2023 to March 2025.
* Only one individual stock, Reliance, is included as a stock-specific explanatory variable.
* The OLS model explains only a relatively small proportion of NIFTY return variation.
* Heteroskedasticity is present in the residuals.
* The residuals are not normally distributed.
* Other potentially important market and macroeconomic variables are not included in the model.
* The analysis focuses on linear relationships and does not capture more complex nonlinear or time-varying relationships.

---

## Future Scope

Future extensions could include:

* GARCH modeling for time-varying volatility
* ARMA-GARCH models
* VAR analysis
* Additional macroeconomic variables
* Interest rates
* Inflation
* Foreign institutional investment
* Additional stocks from the NIFTY 50
* Longer historical periods
* Robust standard errors
* Nonlinear and machine-learning approaches
* Value-at-Risk and Expected Shortfall modeling

---

## Author

**Mansi Sapariya**

MSc Data Science
Christ (Deemed to be University), Bangalore

---

## Disclaimer

This repository is an academic project created for educational and research purposes.

The analysis is not financial advice and should not be used as the sole basis for investment decisions.
