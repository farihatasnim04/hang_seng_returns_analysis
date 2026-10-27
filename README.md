# hang_seng_returns_analysis
Testing whether Hang Seng Index daily returns are normally distributed, plus Monte Carlo option pricing
# Hang Seng Index: Are Daily Returns Normally Distributed?

An empirical test of the normality assumption using 2,654 daily closing prices of the Hang Seng Index (^HSI), followed by a Monte Carlo option-pricing check against Black–Scholes.

Author: Fariha Tasnim · October 2026

## Question
Many standard finance models assume that daily returns follow a log-normal distribution. Do Hang Seng Index returns?

## Data
- Source: Yahoo Finance via the yfinance Python package
- Period: 2016-01-04 to 2026-10-16
- 2,654 trading days; daily log returns

## Part 1: Test of normality
| Measure | Value |
| --- | --- |
| Mean daily log return | 0.00005 |
| Standard deviation (daily) | 0.01377 |
| Skewness | −0.371 |
| Excess kurtosis | 7.154 |
| Days beyond 3 SD | 24 (7.2 expected if normal) |
| Days beyond 4 SD | 10 (0.17 expected if normal) |
| Jarque–Bera statistic | 5,718.45 (p < 0.001) |

Finding: returns have much heavier tails than a normal distribution, and extreme days occur far more often than normality predicts.

## Part 2: Option pricing
Priced a one-year at-the-money call by Monte Carlo (geometric Brownian motion) and compared with Black–Scholes.
- S0 = K = 24,186.83, T = 1 year, r = 3% (assumed), sigma = 0.2186
- Black–Scholes price: 2,450.58 index points
- Monte Carlo price (1,000,000 paths): 2,451.35 (difference 0.76, about 0.03%)

Both methods assume normal returns, which Part 1 contradicts, so these are model prices, not market prices.

## Files
- `hang_seng_returns.ipynb`: all code with outputs
- `Hang_Seng_Returns_Report.pdf`: full written report
- `price_chart.png`, `histogram.png`, `qq_plot.png`, `option_convergence.png`: figures
- `results_summary.csv`, `option_results.csv`: results tables

## How to run
Open the notebook in Google Colab and choose Runtime → Run all. Results can differ slightly as new data becomes available, because the data is downloaded live.

## Limitations
One index, one period; the test is very sensitive with large samples; volatility clustering was observed but not formally tested; option prices use constant volatility, an assumed 3% rate and no dividends.

## About this project
Completed in October 2026 as self-directed learning in Python and quantitative finance. I worked through free courses and used an AI assistant for guidance on the code and for drafting the report. I can explain each step.
