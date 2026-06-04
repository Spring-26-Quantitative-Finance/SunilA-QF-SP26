# Quantitative Finance Project Repo

## Project 1 - Efficient Frontier
7 stocks were selected, their 2-year daily price data was collected and Markowitz Efficient Frontier theory or Mean-Variance Theory was used to determiine the best risk-return combinations for different portfolio weights.
> The Mean-Variance Theory says that any investor will choose the optimal portfolio from the set of portfolios that
> - Maximize expected return for a given level of risk, and
> - Minimize risk for a given level of expected return

**Deliverables**:
- [notebook](project1/main.ipynb)
- [report](project1/efficient-frontier-report.pdf)
- [efficient frontier correlation matrix](project1/outputs/efficient_frontier_correlation_matrix.png)
- [efficient frontier scatter plot](project1/outputs/efficient_frontier_frontier.png)
- [min volatitliy weights](project1/outputs/efficient_frontier_optimal_min_vol_weights.csv)
- [optimal sharpe weights](project1/outputs/efficient_frontier_optimal_sharpe_weights.csv)

## Project 2 - Portfolio Analysis
Project 2 was about comparison. Again, a portfolio of 7 NYSE traded assets were selected. Each stocks were compared invididual against major ETFs: DIA(Dow Jones), SPY(S&P 500), and IWM(Russel). The seven stocks were turned into a portfolio using equal weights and again compared against the same three ETFs.  Finally, a correlation matrix showing the correlations of the portfolio against the ETFs and the individual stocks was prepared.

Some of the factors looked into include: 
- correlation between your portfolio and each ETF
- covariance against each ETF
- tracking error
- Sharpe ratio using the current risk-free rate
- volatility spread between your portfolio and each ETF

**Deliverables**:
- [notebook](project2/main.ipynb)
- [report](project2/proj2-report.pdf)
- [cumulative returns of portfolio against the three ETFs](project2/cumulative-protf-vs-etfs.png)
- [correlation matrix](project2/corr-matrix.png)

## Final Project - Berry Cox momentum long-short portfolio basket
Finally, Berry Cox's price momentum factors were used to select stocks for a long-short portfolio, the stock prices were rebalanced at the end of each month, and finally the algorithm was backtested using five years of historical data.

Factors worked on include:
- 52-week trend
- percentage above 260-day low
- 4-week/52-week price oscillator
- 39-week return
- 51-week volume price trend

###### z-score selection
The z-scores were combined into a final score as:
```python
combined_z_score = (
    z_trend_52w
    + z_pct_above_260_low
    + z_price_oscillator_4w_52w
    + z_return_39w
    + z_vpt_51w
) / 5
```
While the above was the simplest/baseline combination that was used. 

The optimal result appeared when `z_vpt_51w`, which was the least correlated (*concept borrowed from project 2*) to the other 4 factors, was assigned 50% of weight in the final score. This and the assigning of weights, using Monte Carlo Simulation, gave us the best result. This part doesn't appear in the report, the change from the other branch will be merged at the end.

**Deliverables**:
- [notebook](final_proj/main.ipynb)
- [report](final_proj/fina-proj-report.pdf)
- [portfolio cumulative return equal-weighted vs ETF](final_proj/figures/cumulative-return-longshort-portfolio-vs-ETF-equal-weighted.png)
- [porfolio cumulative return optimized-weighted vs ETF](final_proj/figures/cumulative-return-longshort-portfolio-vs-ETF-optimized.png)
- [monthly long-short return equal-weighted vs ETF](final_proj/figures/monthly-longshort-portfolio-return-vs-etf-equal-weighted.png)
- [monthly long-short return optimized-weighted vs ETF](final_proj/figures/monthly-longshort-portfolio-return-vs-ETF-optimized.png)
- [monthly return equal-weighted long-picks vs short-picks vs ETF](final_proj/figures/monthly-return-longpicks-vs-short-picks-vs-ETF-equal-weighted.png)
- [monthly return optimized-weighted long-picks vs short-picks vs ETF](final_proj/figures/monthly-returns-long-picks-vs-short-picks-vs-ETF-optimized.png)

Note: these figures captures the results gained using[ `combined_z_score`](#z-score-selection) that give all factors the same weight(`0.20`).
