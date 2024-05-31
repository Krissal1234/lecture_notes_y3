Financial markets

A market is a place where traders gather to trade instruments

Basic functions:
- To bring buyeres and sellers together -- has change little over time, but the market faccility withn which trading takes place has been greatly influence by tech
- The market may consist in a physical trading floor, or it may be an electronic system in which traders can easily communicate with each other

Market microstructure examines organised trading in instruments. Instruments include common stocks, preferred stocks, bonds, convertible bonds, warrants, options, future contracts, forward contracts etc ..

In a trading market, assets are not transformed (as they are by banks that transform deposits into loans) but they are simply transferred from one investor to another


#### Market Microstructure and Trading

Trading is a search problem. Buyers must find sellers, and sellers must fund buyers

- Every trader wants to trade at a good price
	- Sellers seek buyers willing to pay high prices
	- Buyers seek sellers willing to sell at low prices
	- Traders must also find traders who are willing to trade quantities, or sizes they desire

Stocks  represent only about 20% of the capital wealth of the US. Most of the wealth is in real estate, which rarely trades

#### Players
- Brokers trade on behalf of their clients
- investment sponsors - pention funds, mutual funds, trusts and foundations that invest money
- investment sponsors employ investment advisors to manager their funds
- investment advisers employ traders to implement their strategies and these traders are called buy side traders
- The beneficiaries ultimately benefit from the funds that investment sponsors hold
- Dealer is a person who will buy and sell securities on their account


- Traders have **long positions** when they own something. Traders with long positions profit when prices rise. They try to buy low and sell high.

- Traders have **short positions** when they have sold something that they do not own. Traders with short positions hope that prices will fall so that they can repurchase at a lower price. When they repurchase, they cover their positions. Short sellers profit when they sell high and buy low.
	- Short selling involves borrowing a security whose price you think is going to fall and then selling it on the open market. You then buy the same stock back later, hopefully for a lower price than you initially sold it for, return the borrowed stock to your broker, and pocket the difference.
		- For example, let's say a stock is trading at $50 a share. You borrow 100 shares and sell them for $5,000. The price subsequently declines to $25 a share, at which point you purchase 100 shares to replace those you borrowed, netting $2,500.


Buy side: consists of traders who buy exchange services. Liquidity is the most important of these services. Liquidity is the ability to trade when you want to trade

Sell side: refers to the part of the industry that is involve in the creation, promotion and sale of stocks, bonds and other financial instruments. Sell side individuals and firms work to create and service products that are made available to the buy side of the industry. the sell side provide the liquidity

![[Pasted image 20240516163706.png]]


![[Pasted image 20240516163727.png]]

### Speculative Trading
From a Machine learning perspective, our interest is mostly in speculative trading

Harris (2002) defines speculators as traders who trade to profit from information and predictions about future prices
- This also depends on the accuracy of this information

This makes technical analysis a more adequate tool and rests on the underlying assumption that prices
move in trends (hence asserting price momentum). 
- Typically, technical traders apply a set of technical indicators, which normally consist in an arsenal of statistical measures and charts (or machine learning algorithms), to assist with the analysis of the noisy price time series and with the prediction of short-termmarket moves.

### Types of Trading sessions

**continuous markets:** traders may trade anytime the market is open
**call markets:** all traders trade at the same time when the market is called. The market may call all securities simulataneously or it may call the securities one at a time, in rotation

Markets utilize time matching orders with order precedence rules.

The main advantage of **continuous trading** is that it allows traders to attempt to
arrange their trades whenever they want.

The main advantage of **call markets** is that they focus the attention of all traders
interested in a given instrument at the same time and place.


Orders
- Orders are instructions that traders give to brokers and exchanges which arrange their trades 
![[Pasted image 20240516164353.png]]


### Market orders

These are orders that are traded at the best price currently available in the market

you pay the bid/ask price spread in a round trip

Market orders are characterised by execution price uncertainty

![[Pasted image 20240516164520.png|400]]


### Limit Orders

A limit order is an instruction to trade at the best price available, but only if it is no worse than the limit price specified by the trader

Buy orders: the trade price must be at or below the limit price 
sell orders: the trade price must be above the limit price


![[Pasted image 20240516165230.png]]


## The Trading Process

Johnsonn(2010) divides the trading process into three stages:
(i) Price formation
(ii) price discovery and trade execution
(iii) reporting, clearing and settlement


#### Price Formation

Price formation is the process through which the price of an asset is determined - evaluating a fair price of something

Since different investors tend to have different views in terms of asset valuation, price formation is the result of supply and demand conditions


#### Price discovery
price discovery happens when supply and demand requirements intersect, hence determining the price of an asset

The constant tension between butyesr and sellers dictates the dynamic movement of market prices



## Technical Analysis

Different tools
- Technical analysts believe that a stock price includes enough information to not need to analyse a company's financial statements
- They focus on the stock chart for hints into where the price may be headed

![[Pasted image 20240516170953.png]]

Chartist: these people analyse price charts only
technical analysts: study technical indicators derived from price changes in addition to price charts.

Technical analysts  examine the price action of the financial markets instead of the fundamental factors that effect market prices
- Technicians believe that even if all relevant information of a particular market or stock was available, you could not predict a precise market "response" to that information



![[Pasted image 20240524175458.png]]
The image is an example of an "Order Book" for a financial instrument, specifically the SPDR S&P 500 ETF TR TR UNIT. An order book is a real-time list of buy and sell orders in a financial market.
### Key Elements of the Order Book:

1. **Orders Accepted**:
    
    - The total number of orders that have been accepted. In this example, it is 1,153,586.
2. **Total Volume**:
    
    - The total trading volume of the instrument. Here, it is 7,689,062.
    - **Volume**: The total number of shares or contracts traded in a security or market during a given period. It indicates the activity level and liquidity of the instrument.

- **Volume**: Reflects the actual trading activity (completed trades).
- **Orders**: Reflects the intention to trade (pending or unexecuted trades).

- **Volume**: Provides information about market activity and liquidity.
- **Orders**: Provides information about the current market depth, supply, and demand.

1. **Top of Book**:
    
    - This section shows the top five buy (bid) and sell (ask) orders.
        
    - **Asks**:
        
        - These are sell orders. Each row shows the number of shares available for sale at a specific price.
        - Example: 11,000 shares are available at a price of 180.07.
    - **Bids**:
        
        - These are buy orders. Each row shows the number of shares buyers are willing to purchase at a specific price.
        - Example: 6,400 shares are desired at a price of 180.02.
4. **Last 10 Trades**:
    
    - This section lists the details of the most recent 10 trades that have occurred.
    - Columns include:
        - **Time**: The exact time the trade occurred.
        - **Price**: The price at which the trade was executed.
        - **Shares**: The number of shares traded.

### Detailed Breakdown of the Example:

- **Asks (Sell Orders)**:
    
    - 11,000 shares at $180.07
    - 12,500 shares at $180.06
    - 12,900 shares at $180.05
    - 9,700 shares at $180.04
    - 1,100 shares at $180.03
- **Bids (Buy Orders)**:
    
    - 6,400 shares at $180.02
    - 9,700 shares at $180.01
    - 9,600 shares at $180.00
    - 14,700 shares at $179.99
    - 11,500 shares at $179.98
- **Last 10 Trades**:
    
    - Trades occurred between 14:42:06 and 14:42:13.
    - Prices ranged from $180.00 to $180.03.
    - Trade sizes were mostly 100 shares, with one trade of 200 shares.

### Usage:

This order book provides traders with critical information about the current market depth, showing the supply and demand at various price levels. It helps them make informed decisions on their trades.

For more examples and live data, you can visit financial market websites like Binance.com, which provide real-time order books for various financial instruments.






Volatility
- It does not measure the direction of price changes but merely their dispersion
- Two instruments with different volatilities may have the same expected return but the one with higher volatility will have large swingsg in values over a given period of time




Efficient Market Hypothesis (EMH)

- It is made up of three progressively stronger forms
	- Weak form
	- Semi-Strong Form
	- Strong form

#### Weak Form
- this form says that the past prices, volume and other market statistics provide no information that can be used to predict future prices
- If stock prices are random, then past prices cannot be used to forecast future prices.
	- Price changes should be random  because it is information that drives these changes, and information arrives randomly
- This form of EMH, is correct, repudiates technical analysis
- Most research supports the notion that the markets are weak form efficient

#### Semi-String Form
- This form says that prices fully reflect all publicly available information and expectations about the future
- It suggests that prices adjust very rapidly to new information, and that old information cannot be used to earn superior returns.
- If this form is correct, repudiates fundamental analysis
- Most studies find that the markets are reasonably efficient in this sense, but the evidence is somewhat mixed

#### Strong Form
- This form says that prices fully reflect all information, whether publicly available or not
- Even the knowledge of material, non-public information cannot be used to earn superior results
- Most studies have found that the markets are not efficient in this sense
![[Pasted image 20240524210822.png]]

![[Pasted image 20240524211214.png]]![[Pasted image 20240524211246.png]]The image explains the concept of stationarity in time series data. For a time series to be considered stationary, certain statistical properties must remain constant over time. The image illustrates three key properties of stationarity using graphs:

### 1. Mean of the Series:

- **Stationary Series (Green Graph)**:
    
    - The mean (average value) of the series remains constant over time.
    - In the green graph, the data fluctuates around a constant mean level.
- **Non-Stationary Series (Red Graph)**:
    
    - The mean changes over time, indicating a trend.
    - In the red graph, the mean increases as time progresses, making the series non-stationary.

### 2. Variance of the Series:

- **Stationary Series (Green Graph)**:
    
    - The variance (spread or volatility) of the series is constant over time.
    - In the green graph, the fluctuations in the data have a consistent amplitude.
- **Non-Stationary Series (Red Graph)**:
    
    - The variance changes over time, indicating changing volatility.
    - In the red graph, the spread of the data increases and decreases over time, making the series non-stationary.
### 3. Covariance of the Series:

- **Stationary Series (Green Graph)**:
    
    - The covariance (measure of how much two variables change together) between terms is constant over time.
    - This means the relationship between the values at different times remains consistent.
- **Non-Stationary Series (Red Graph)**:
    
    - The covariance changes over time, indicating that the relationship between terms varies.
    - In the red graph, the spread between points changes over time, showing that the covariance is not constant.

### Summary:

For a time series to be stationary, it must satisfy the following conditions:

1. **Constant Mean**: The mean should not change over time.
2. **Constant Variance**: The variance should not change over time.
3. **Constant Covariance**: The covariance between terms should remain constant over time.

Stationarity is crucial for many statistical and econometric models because non-stationary data can lead to unreliable and spurious results. Stationary data allows for more reliable modeling, forecasting, and hypothesis testing.

![[Pasted image 20240524211538.png]]
### White Noise

#### Definition:

- A time series {wt:t=1,…,n} is considered to be **discrete white noise** if:
    - The variables of the series are independent and identically distributed (i.i.d.).
    - The mean of the series is zero.
    - The variance is constant over time.
    - There is no serial correlation, meaning the correlation between any two different time points is zero.
#### Mathematical Representation:

1. **Mean**:
    
    - $μ_w=E(w_t)=0$
    - This indicates that the expected value (mean) of the series $w_t$​ is zero.
2. **Variance**:
    
    - The variance of the series is constant over time, although this is not explicitly stated in the equation, it is implied in the definition of white noise.
3. **Serial Correlation**:
    
    ![[Pasted image 20240524211922.png]]
    - This means that the correlation of the series with itself (autocorrelation) is 1 at lag 0 (the same time point), and 0 at any other lag k. There is no correlation between different time points, indicating that each value in the series is independent of the others.

#### Gaussian White Noise:

- When the elements of the time series are drawn from a standard normal distribution $i.e., $wt∼N(0,σ2))$, the series is known as **Gaussian white noise**.
    - Here, $N(0,σ2)$ denotes a normal distribution with mean 0 and variance σ2

### Key Point in Time Series Modelling:

- When building models for time series, the goal is to explain the serial correlation in the observations. If a model is successful, the residuals (errors) from the model should themselves be uncorrelated.
- **Residuals as White Noise**:
    - If the residuals are serially uncorrelated, they can be considered white noise.
    - This indicates that the model has effectively captured the underlying patterns in the data, and what remains is random noise.