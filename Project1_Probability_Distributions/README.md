
# Statistical Modelling of Equity Returns

## Overview

This project investigates the statistical properties of Apple
(AAPL) weekly log returns and compares Gaussian and Student's
t-distribution models.

The objective is to evaluate whether greater distributional
flexibility improves the modelling of historical equity returns
and generalises to unseen observations.

## Research Question

Does a Student's t-distribution describe AAPL weekly returns
more effectively than a Gaussian distribution, both in-sample
and out-of-sample?

## Dataset

- Asset: Apple Inc. (AAPL)
- Period: September 2019 – September 2024
- Frequency: Weekly
- Observations: 261 prices and 260 log returns
- Source: Yahoo Finance, via yfinance

Weekly log returns are calculated as:

r_t = ln(P_t / P_(t-1))

## Methodology

1. Load historical equity price data.
2. Calculate weekly logarithmic returns.
3. Examine descriptive statistics and empirical distributions.
4. Estimate Gaussian and Student's t-distribution parameters
   using maximum likelihood estimation.
5. Compare in-sample fit using AIC and BIC.
6. Evaluate models using a chronological 80/20 split.
7. Perform five expanding-window validation experiments
   using non-overlapping 26-week test periods.

## Results

### Descriptive Statistics

| Statistic | Result |
|---|---:|
| Mean weekly log return | 0.005542 |
| Standard deviation | 0.040144 |
| Skewness | -0.4817 |
| Excess kurtosis | 2.5952 |

### In-Sample Model Comparison

| Metric | Gaussian | Student's t |
|---|---:|---:|
| AIC | -931.0968 | -946.3904 |
| BIC | -923.9755 | -935.7084 |

Both criteria favour Student's t.

### Chronological Hold-Out Evaluation

| Model | Test log-likelihood |
|---|---:|
| Gaussian | 101.9933 |
| Student's t | 103.2795 |

Student's t marginally outperformed the Gaussian on the
final 52 observations.

### Expanding-Window Validation

Across five non-overlapping test windows:

- Student's t outperformed the Gaussian in 3 of 5 windows.
- The aggregate Student's t minus Gaussian log-likelihood
  difference was -1.6058.
- The Gaussian achieved slightly better aggregate performance.

## Conclusion

Student's t provides a better full-sample fit according
to AIC and BIC, but its predictive advantage is not
consistent across chronological validation periods.

The findings highlight the importance of distinguishing
in-sample model fit from out-of-sample generalisation.

## Limitations

- Only one equity is studied.
- Results depend on the selected historical period.
- Both models assume an unconditional return distribution.
- Neither model captures time-varying volatility directly.
- The symmetric Student's t-distribution does not explicitly
  model the observed negative skewness.
- No trading strategy or investment profitability is evaluated.

## Technologies

Python, NumPy, Pandas, SciPy, Matplotlib, Jupyter

## Research Notebook

[View the Jupyter notebook](Probability_Distributions.ipynb)

## Future Extensions

- Evaluate additional equities and market regimes.
- Investigate volatility clustering and conditional models.
- Compare rolling-window and expanding-window estimation.
- Introduce systematic equity signals and backtesting.

## Disclaimer

This project is for educational and research purposes only.
It does not constitute investment advice.
