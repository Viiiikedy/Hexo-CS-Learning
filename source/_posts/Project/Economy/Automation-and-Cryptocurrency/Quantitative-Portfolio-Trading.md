---
title: Quantitative Portfolio Trading
tags: Automatic Trading & Cryptocurrency
date: 2023-09-11 10:15:38
---
<style>
    .image-container {
        display: flex;
        justify-content: space-between; /* 让图片均匀分布在一行中 */
        position: relative;
    }
    .menu-item {
        display: inline-block; /* Ensure elements are horizontally aligned */
        margin-right: 20px;
        position: relative;
        padding: 5px;
        color: grey;
        text-decoration: none;
        font-size: 90%; /* Reduce font size */
    }
    .menu-item:hover {
        font-weight: bold;
        color: grey !important;
    }
    .menu-item::before {
        content: counter(item) " ";
        counter-increment: item;
        border: 1px solid black;
        background-color: transparent;
        border-radius: 50%;
        width: 20px;
        height: 20px;
        display: inline-block;
        text-align: center;
        line-height: 20px;
        margin-right: 1px;
        color: grey;
    }
    .menu-list {
        list-style: none; 
        counter-reset: item;
        padding: 0; /* Remove default padding */
    }
    .menu-list div {
        white-space: nowrap; /* Prevent wrapping of list items */
    }
</style>

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Economy&Business](/2023/09/11/Project/Economy/Economy/index.html) > [Automatical Trading and Cryptocurrency](/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html) > **[Quantitative Portfolio Trading](/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html)</small>***
<ol class="menu-list">
    <div>
        <li><strong><a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html" class="menu-item">Quantitative Portfolio Trading&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong>
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Decentralized-Cryptocurrency-Exchange" class="menu-item">Decentralized CryptoCurrency Exchange&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Derivative-Mathematical-Pricing" class="menu-item">Derivative Mathematical Pricing&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>

---

<h3 id="python-section">Project1: Quantitative Factor Mining, Tracking, and Prediction</h3>

In the fast-paced financial environment,quantitative analysis plays an important role on both <u>monitoring and predicting the timely data</u> from the secondary markets. Here I include 3 of my past projects on the related topics:
>- Project 1:[Fundamental Market Forecast Using Talib](https://drive.google.com/file/d/1BHi_7FbfDPFedQQLFEoSrbZ8DUURodWr/view?usp=sharing)
>- Project 2:[Real Time Monitoring of Secondary Market Information](https://drive.google.com/file/d/12_vKPmFFMUEwPwJRzPLZxfWnLWUt9V4l/view?usp=sharing)
>- Project 3:[Factor-based Trading and Hedging on Quantitative Platforms](/pdf/Quants-in-Chinese.pdf)

<div class="image-container">
    <img src="https://s2.loli.net/2024/01/06/NRwxXyhQ1AngIfp.png" width="40%" height="40%">
    <img src="https://s2.loli.net/2024/01/06/Kue3R7ykWsiNvH9.png" width="40%" height="40%">
</div>
<h3 id="vba-section">Project2: Financial Valuation by VBA</h3>

[VBA](https://learn.microsoft.com/en-us/office/vba/library-reference/concepts/getting-started-with-vba-in-office) is important particularly in linking multiple financial statements and conducting valuations involving a series of formulas, such as DCF, LBO, and M&A, familiarity with Excel programs and functions can significantly enhance efficiency.
> Project Address:[here](/zip/Full-Financial-Model.xls)

### Project3: JP Morgan Private Bank:Quantitaive Asset Allocation Strategy
We applied statistical analysis, risk management techniques, and portfolio optimization models. Utilizing algorithms, macroeconomic analysis, and asset class research, we made informed investment decisions, adhering to legal and regulatory standards.
> Project Report:[here](/pdf/Asset-Allocation-Proposal-JP-Private-Bank-Competition.pdf)
> Project Code:[here](https://colab.research.google.com/drive/1qvlPVViL0AX2eK774DtjTbQNB9IRThCL?usp=sharing)

- Strategic Allocation
- Tactical Allocation
- Scenario Analysis
- Investment Implementation
- Requirements Achievement

### Project4:Pair Trading Strategy
This is a market-neutral trading strategy that involves matching a long position with a short position in two stocks with a high correlation. The following is used in my past research for tthis strategy.
```python
import numpy as np
import pandas as pd
from jqdata import *

# Industry ID
instruments_code_bank = get_industry_stocks('I64')[0:15]
prices_temp = pd.DataFrame()
start_date = '2020-01-01'
end_date = '2022-04-29'
for c in instruments_code_bank:
    c_daily = get_price(c, start_date, end_date)
    c_daily['code'] = c
    prices_temp = pd.concat([prices_temp, c_daily])

prices_temp_code_close = prices_temp[['code', 'close']]
# prices_temp_code_close
mode_num = np.argmax(np.bincount([len(i) for i in [prices_temp_code_close[prices_temp_code_close.code == c] for c in instruments_code_bank]]))
# Create a dictionary to index the closing price of this year by ts_code
price_dict_all = dict(list(prices_temp_code_close.groupby('code')['close']))
# Filter out the stocks in the dictionary whose trading dates equal the mode number, so as to analyze more pairs with high correlation in the stock pool
price_dict = dict(filter(lambda x: len(x[1]) == mode_num, price_dict_all.items()))
instruments_code = list(price_dict.keys())

import matplotlib.pyplot as plt
import statsmodels.api as sm
import seaborn as sns

# Calculate correlation
def get_pearson_r(price_dict):
    n = len(price_dict)
    keys = list(price_dict.keys())
    r_matrix = np.ones((n, n))
    for i in range(n):
        stock1 = price_dict[keys[i]]
        for j in range(i+1, n):
            stock2 = price_dict[keys[j]]
            r = stock1.corr(stock2)
            r_matrix[i, j] = r
    return r_matrix

# Input is a price_dict, each column is the price of a stock on each day
def find_cointegrated_pairs(price_dict):
    # Get the length of price_dict
    n = len(price_dict)
    # Initialize the p-value matrix
    pvalue_matrix = np.ones((n, n))
    # Extract column names
    keys = list(price_dict.keys())
    mode_num = np.argmax(np.bincount([len(i) for i in list(price_dict.values())]))
    # print("keys:",keys)
    # Initialize strong cointegration group
    pairs = []
    # For every i
    for i in range(n):
        # For j greater than i
        stock1 = price_dict[keys[i]]
        if len(stock1) != mode_num:
            continue
        for j in range(i+1, n):
            # Get the price Series of the respective two stocks
            stock2 = price_dict[keys[j]]
            if len(stock2) != mode_num:
                continue
            # Analyze their cointegration relationship
            result = sm.tsa.stattools.coint(stock1, stock2)
            # Extract and record the p-value
            pvalue = result[1]
            pvalue_matrix[i, j] = pvalue
            # If the p-value is less than 0.05
            if pvalue < 0.05:
                # Record the stock pair and the corresponding p-value
                pairs.append((keys[i], keys[j], pvalue))
    # Return the result
    return pvalue_matrix, pairs

pvalues, pairs = find_cointegrated_pairs(price_dict)
pairs_df = pd.DataFrame(pairs, index=range(0, len(pairs)), columns=list(['comp1', 'comp2', 'pvalue']))
# The smaller the pvalue, the greater the correlation, ranking by ascending pvalue gets the stock pairs with high correlation from high to low
pairs_df = pairs_df.sort_values(by='pvalue')
pairs_df

# %matplotlib inline
plt.rcParams['figure.figsize'] = [15, 8]
sns.heatmap(1-pvalues, xticklabels=instruments_code, yticklabels=instruments_code, cmap='RdYlGn_r', mask=(pvalues == 1))

# The redder in the heatmap, the higher the correlation, indicating the smaller the p-value.

company_choose = [pairs_df.iloc[0].comp1, pairs_df.iloc[0].comp2]
print(company_choose)
x = price_dict[company_choose[0]]
y = price_dict[company_choose[1]]
x = np.log(x)
X = sm.add_constant(x)
y = np.log(y)
result = (sm.OLS(y, X)).fit()
result.summary()

import matplotlib.pyplot as plt
p1 = get_price('000676.XSHE', start_date, end_date, fields='close')
# Drawing the fitting line:

st = np.log(y) - np.log(x) * 1.3584    
fig, ax = plt.subplots(figsize=(8,6))
ax.plot(x, y, 'o', label="data")
ax.plot(x, result.fittedvalues, 'r', label="OLS")
ax.legend(loc='best')

# Set the thresholds for opening and closing positions, here using multiples of standard deviation as an example
open_num = 1.5 # Opening threshold, open positions when the residual is more than 1.5 standard deviations above the mean
close_num = 0.5 # Closing threshold, close positions when the residual is less than 0.5 standard deviations below the mean

# Determine trading signals based on the residual series and record daily position and profit situations
position = 0 # Initial position is 0, indicating no holdings; a position of 1 indicates going long on x and short on y; a position of -1 indicates going short on x and long on y.
capital = 1000000 # Initial capital of 1 million
fee_rate = 0.0005 # Transaction fee rate of 0.0005

trade_log = [] # Record trade log

for i in range(len(resid)):
    if position == 0: # When there are no holdings, determine whether to open positions
        
        if resid[i] > mean + open_num * std: # If the residual is above the upper limit, go short on x and long on y
            
            position = -1 # Position changes to -1
            
            x_price = x[i] * (1 + fee_rate) # Calculate the purchase price of x (considering transaction fees)
            y_price = y[i] * (1 - fee_rate) # Calculate the selling price of y (considering transaction fees)
            
            x_amount = capital / 2 / x_price # Calculate the quantity of x to buy
            y_amount = capital / 2 / y_price # Calculate the quantity of y to sell
            
            trade_log.append([i, 'Open', -1, x_price, y_price, x_amount, y_amount]) # Record trade log
            
        elif resid[i] < mean - open_num * std: # If the residual is below the lower limit, go long on x and short on y
            
            position = 1 # Position changes to 1
            
            x_price = x[i] * (1 - fee_rate) # Calculate the selling price of x (considering transaction fees)
            y_price = y[i] * (1 + fee_rate) # Calculate the purchase price of y (considering transaction fees)
            
            x_amount = capital / 2 / x_price # Calculate the quantity of x to sell
            y_amount = capital / 2 / y_price # Calculate the quantity of y to buy
            
            trade_log.append([i, 'Open', 1, x_price, y_price, x_amount, y_amount]) # Record trade log
    
    elif position == -1: # When short on x and long on y, determine whether to close positions
        
        if resid[i] < mean + close_num * std: # If the residual is below the closing threshold, close positions
            
            position = 0 # Position changes to 0
            
            x_price = x[i] * (1 - fee_rate) # Calculate the selling price of x (considering transaction fees)
            y_price = y[i] * (1 + fee_rate) # Calculate the purchase price of y (considering transaction fees)
            
            trade_log.append([i, 'Close', 0, x_price, y_price]) # Record trade log
    
    elif position == 1: # When long on x and short on y, determine whether to close positions
        
        if resid[i] > mean - close_num * std: # If the residual is above the closing threshold, close positions
            
            position = 0 # Position changes to 0
            
            x_price = x[i] * (1 + fee_rate) # Calculate the purchase price of x (considering transaction fees)
            y_price = y[i] * (1 - fee_rate) # Calculate the selling price of y (considering transaction fees)
            
            trade_log.append([i, 'Close', 0, x_price, y_price]) # Record trade log

# Convert the trade log into DataFrame format and calculate the profit and cumulative profit for each transaction
trade_log = pd.DataFrame(trade_log, columns=['Date', 'Operation', 'Position', 'x Price', 'y Price', 'x Quantity', 'y Quantity'])
trade_log['Profit'] = 0
trade_log['Cumulative Profit'] = 0
for i in range(1, len(trade_log)):
    if trade_log.loc[i, 'Operation'] == 'Close':
        trade_log.loc[i, 'Profit'] = (trade_log.loc[i-1, 'x Price'] - trade_log.loc[i, 'x Price']) * trade_log.loc[i-1, 'x Quantity'] + (trade_log.loc[i, 'y Price'] - trade_log.loc[i-1, 'y Price']) * trade_log.loc[i-1, 'y Quantity']
        trade_log.loc[i, 'Cumulative Profit'] = trade_log.loc[i-1, 'Cumulative Profit'] + trade_log.loc[i, 'Profit']
    else:
        trade_log.loc[i, 'Cumulative Profit'] = trade_log.loc[i-1, 'Cumulative Profit']

# Print trade log
print(trade_log)

# Plotting Cumulative Return Curve
plt.plot(trade_log['Date'], trade_log['Cumulative Profit'])
plt.xlabel('Date')
plt.ylabel('Cumulative Return')
plt.title('Market Neutral Strategy')
plt.show()
```
### Quantitative Trading Platform Recommendation

Here I will recommend some quant platforms that I always use:
- [Portfolio123](https://www.portfolio123.com/)
- [Ricequant](https://www.ricequant.com/welcome/)
- [Bigquant](https://bigquant.com/)

