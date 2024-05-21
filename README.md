# Quantitative Investing Strategies

This project demonstrates two quantitative investing strategies: a momentum strategy and a value strategy. Each strategy involves selecting 50 stocks from the S&P 500 based on specific criteria and calculating recommended trades for an equal-weight portfolio of these stocks, as well as more advanced strategies.

## Table of Contents
- [Introduction](#introduction)
- [Library Imports](#library-imports)
- [Importing Stock Data](#importing-stock-data)
- [Making API Calls](#making-api-calls)
- [Quantitative Momentum Strategy](#quantitative-momentum-strategy)
  - [Filtering High Momentum Stocks](#filtering-high-momentum-stocks)
  - [Advanced Momentum Strategy](#advanced-momentum-strategy)
- [Quantitative Value Strategy](#quantitative-value-strategy)
  - [Filtering Value Stocks](#filtering-value-stocks)
  - [Advanced Value Strategy](#advanced-value-strategy)
- [Calculating Shares to Buy](#calculating-shares-to-buy)
- [Saving to Excel](#saving-to-excel)
- [Calculating Returns](#calculating-returns)
- [Investment Strategy using 80-20 Principle](#investment-strategy-using-80-20-principle)
- [Visualizing Returns](#visualizing-returns)
- [Acknowledgements](#acknowledgements)

## Introduction

This project builds two separate investing strategies:
- **Momentum Investing**: Investing in stocks that have increased in price the most.
- **Value Investing**: Investing in stocks that are cheapest relative to common measures of business value (like earnings or assets).

Each strategy selects the 50 best stocks based on their criteria and calculates recommended trades for an equal-weight portfolio of these stocks, as well as more advanced strategies.

## Library Imports

The project utilizes the following libraries:
- `numpy`
- `pandas`
- `requests`
- `math`
- `scipy.stats`
- `xlsxwriter`

## Importing Stock Data

We import a list of S&P 500 stocks from a CSV file.

## Making API Calls

The project uses the IEX Cloud API to fetch the necessary data for the two strategies.

## Quantitative Momentum Strategy

### Filtering High Momentum Stocks

The top 50 stocks by one-year price return are selected and sorted.

### Advanced Momentum Strategy

The strategy is refined by considering high-quality momentum, selecting stocks from the highest percentiles of:
- 1-month price returns
- 3-month price returns
- 6-month price returns
- 1-year price returns

Each stock is assigned a percentile rank for each timeframe, and the average of these percentiles (HQM score) determines the top momentum stocks.

## Quantitative Value Strategy

### Filtering Value Stocks

The top 50 stocks by combined value metrics are selected and sorted. These metrics include:
- Price-to-earnings ratio (P/E ratio)
- Price-to-book ratio (P/B ratio)
- Price-to-sales ratio (P/S ratio)
- Enterprise value divided by EBITDA (EV/EBITDA)
- Enterprise value divided by gross profit (EV/GP)

### Advanced Value Strategy

The strategy is refined by considering multiple value metrics, selecting stocks from the lowest percentiles of:
- Price-to-earnings ratio
- Price-to-book ratio
- Price-to-sales ratio
- Enterprise value divided by EBITDA (EV/EBITDA)
- Enterprise value divided by gross profit (EV/GP)

Each stock is assigned a percentile rank for each metric, and the average of these percentiles (RV score) determines the top value stocks.

## Calculating Shares to Buy

A function calculates the number of shares to buy for each selected stock based on the given portfolio size.

## Saving to Excel

The results are saved to an Excel file using `xlsxwriter`, with formatted columns for better readability.

## Calculating Returns

The returns for the selected stocks are calculated over different timeframes, using the following steps:
1. **Fetch Historical Price Data**: Retrieve the historical prices for each stock.
2. **Calculate Returns**: Compute the returns for each selected stock over the specified timeframes (e.g., 1 month, 3 months, 6 months, and 1 year).
3. **Aggregate Returns**: Aggregate the returns for the entire portfolio.

## Investment Strategy using 80-20 Principle

An alternative investment strategy based on the 80-20 principle is implemented for the two strategies. In this strategy, 80% of the portfolio size is allocated to the top 20% of stocks based on the HQM or RV Score, and the remaining 20% of the portfolio size is allocated to the rest of the stocks.

The code iterates through the stocks in `hqm_dataframe` or `rv_dataframe` and calculates returns for each timeframe (one month, three months, six months, and one year) using the 80-20 allocation principle. For the top 20% of stocks, 80% of the portfolio size is allocated, and for the remaining 80% of stocks, 20% of the portfolio size is allocated.

Ensure to adjust the `portfolio_size` variable as per your portfolio setup before running the code.

## Visualizing Returns

The project includes a section to visualize and compare the returns of two different investment strategies:
- **Equal Weighting**: Allocating an equal amount of capital to all selected stocks.
- **Unequal Weighting (80-20 Principle)**: Allocating 80% of the portfolio to the top 20% of stocks based on the HQM or RV Score, and 20% to the remaining 80% of stocks.

To visualize the returns, the project uses `matplotlib` to generate a bar graph showing the returns for different timeframes (1 month, 3 months, 6 months, and 1 year).

The steps to generate the visualization include:
1. **Calculate Returns**: Compute the returns for each selected stock over the specified timeframes.
2. **Aggregate Returns**: Aggregate the returns for the entire portfolio under the two strategies.
3. **Plot the Graph**: Use `matplotlib` to create a bar graph comparing the returns of the two strategies.

By visualizing the returns, you can easily compare the performance of the equal-weight and 80-20 principle strategies across different timeframes.

The following graph shows the comparison of returns over different timeframes using the 80-20 investment strategy:

 - Returns Comparison for Quant Momentum Strategy
   
![Returns Comparison for Quant Momentum Strategy](https://i.postimg.cc/2S9991yx/Untitled.png)

 - Returns Comparison for Quant Value Strategy
   
![Returns Comparison for Quant Value Strategy](https://i.postimg.cc/6pBFBWfY/Untitled.png)



## Acknowledgements

This project was developed using the following resources and libraries:
- [IEX Cloud API](https://iexcloud.io/)
- [pandas library](https://pandas.pydata.org/)
- [numpy library](https://numpy.org/)
- [scipy library](https://www.scipy.org/)
- [xlsxwriter library](https://xlsxwriter.readthedocs.io/)
- [matplotlib library](https://matplotlib.org/)
- Special thanks to the creators of the open-source libraries used in this project.
