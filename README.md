# **AlphaGold** - ProjectTwo

## Team Members
---

* Desmond
* Kevin
* Ramesh

## Summary
---
Our project is to develop a system that assist the users to achieve a top-performing and diversified portfolio that allows them to invest in global markets and industries.

In this project, our group will investigate the performance of different ML algorithms in obtaining precise nowcasts of the current gross domestic product (GDP) growth, top industry performers in OECD countries within five years timeframe, and then evaluate the real-time performance of these algorithms to determine an optimal investment portfolio.  

After determining the market fundamentals, industry growth, and market conditions, we will adapt and integrate into the portfolio management by providing our users with an effective trade management system. Such an example is to develop and strategize optimal key entry and exit points in our trading strategies. Followed by backtesting to provide the user with a measure of how well their portfolio performed.

## Scope
---

* [GDP Analysis](#GDP-Analysis-(Nowcasting))
* [Industry Analysis](#Industry-Analysis)
* [Portfolio Creation](#Portfolio-Creation)
* [Trading Strategies & Backtesting](#Trading-Strategies-&-Backtesting)

## Review
---
### Difficulties & Limitations
* Large volume of data
* Metadata and data separation
* Model fitting trial and error
* Neural Network beyond our knowledge
* Software conflicts between libraries
## GDP Analysis (Nowcasting)
---
We attempted multiple models when forecasting GDP. One was KNN which fit well based on the macroeconomics information, however required a large range of feature (X) parameters. Therefore, in the end we settled for the DynamicFactorMQ model.

The data was provided by OECD and covers Australia from 2000 quarter 1 till present, for the following indicators:  
* Balance of Payments
* Business Tendency and Consumer Opinion Surveys
* Composite Leading Indicators
* Financial Statistics Share Price Index
* Financial Statistics Long-Term Interest Rates
* Industry
* International Trade
* Labour Market Statistics
* Consumer Price Indices



![Correlation](/images/gdp_factors_correlation.png) 

![R2](/images/gdp_indicators_r2.png)

![Confidence_Intervals](/images/gdp_confidence_intervals.png)

![Nowcast](/images/gdp_nowcast.png)

## Industry Analysis
---
We then proceeded to get the top 50 stocks from the ASX depending on overall market capitalisation.

This involved in-depth analysis of market metadata and indicators to look at each industry's contribution to the overall GDP.

![Industry_breakdown](/images/industry_breakdown.png)
## Portfolio Creation
---
At this stage we went ahead and further narrowed down to an 8 stock portfolio.

We looked at two strategies:  
1. Heuristic K-Means Clustering Model  
To prepare the data for the model we pulled stock closing price data from yfinance and restructured it to an array. We then computed the mean return, variance and covariance to feed the model. We then arranged the stocks into 8 clusters with the aforementioned characteristics and reattributed the stock labels to their respective numerical value. Finally, running a random choice to select one stock from each cluster to form the user's portfolio.
2. Ratio-Based Model  
Taking into consideration the following ratios:
* Sharpe ratio
* Common Sense ratio
* Conditional Value at Risk
* Expected Return
* Kelly Criterion
* Kurtosis
* Volatility
* Average Return
* Risk of Ruin
* Sortino
* Volatility
* Profit Factor
## Trading Strategies & Backtesting
---
After the user has been built a portfolio of stocks we then provide the trading algorithm and backtesting to evaluate performance.  
### MACD Oscillator  
The Moving Average Convergence/Divergence strategy is rather popular and widely used as a technical indicator for trading. The strategy features a MACD line which is calculated by the difference between a 12-day (fast) and 26-day (slow) exponentially-weighted moving average. This is coupled with a Signal line which is a 9-day moving average of the MACD line, and a Histogram that represents the difference between the two lines.  

![MACD_plot](/images/macd_signals_plot.png)

The buy/sell signals are then based on the crossovers between the MACD and Signal line which we can then feed into our backtester. Finally computing a total portfolio profit of $547,148.55 from 6 months of trading and an initial investment of $100,000.

![Heatmap](/images/macd_heatmap.png)

## Code Submission Folder
* [Code](/code)

## Presentation
* [Alpha Gold Presentation](/presentation/Alpha-Gold_presentation.pdf)

## Libraries
* pandasdmx 
*  requests 
* pandas
* re
* scikitlearn (sklearn)
* statsmodel
* seaborn 
* matplotlb
* numpy
* vectorbt
* hvplot
* yfinance
* quantstats
* Keras (Tensor Flow)
