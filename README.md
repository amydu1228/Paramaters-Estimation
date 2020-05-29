# Paramaters-Estimation

## Goal: 
The goal for this project is to estimate paramaters from CAPM and Fama-French 4-factor models.

## Data:
Use regular expression to collect financial data on onver complete list of banks stock trading on the NYSE from Kenneth French data library, Yahoo Finance, TopForeignStocks.com.

The following features were gathered for each bank:

* Bank Name
* Bank Ticker
* Risk Free Rate
* Small Minus Big (SMB) Factor
* High Minus Low (HML) Factor
* Momentum Factor

Tools & Packages Required
* Python
* Numpy
* Pandas
* Statsmodels
* Requests (HTTP Requests)
* Re (Regular Expression Operations)

## Project Approach:
There are four steps that in this project:

### Step 1: Applied web scraping skills to extract data from multiple external sources
I used regular expression to extract bank name and bank ticker from complete list of banks stock trading on the NYSE at TopForeignStocks.com. The detailed website is https://topforeignstocks.com/stock-lists/the-complete-list-of-bank-stocks-trading-on-the-nyse-2/. 

I also found the complete list of banks stock trading on NASDAQ at the website of https://topforeignstocks.com/stock-lists/the-complete-list-of-bank-stocks-trading-on-nasdaq/. Same regular expression coding can be applied to this link.

### Step 2: Built a OLS CAPM model to estimate Beta
The Capital Asset Pricing Model (CAPM) says that the excess return on an asset is 𝐸(𝑅𝑖)−𝑅𝑓=𝛽𝑖[𝐸(𝑅𝑚)−𝑅𝑓], where 𝑅𝑚 denotes the return on the market portfolio and 𝑅𝑓 denotes the riskfree rate.

Return data on the market portfolio, the risk-free rate, as well as other return factors, is available from Kenneth French's data library https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html, which can be accessed directly using the pandas_datareader.

To estimate a stock's beta, I regress its excess returns on the returns of the market portfolio through OLS. This can be done with the statsmodels package.

### Step 3: Built a OLS Fama-French 4-factor model to estimate Beta, SMB, HML, Momentum
Fama-French 4-factor model adds a size, value, and momentum factor to the standard market portfolio so that returns are better described by a multifactor model.

I also applied OLS regression to calculate excess returns.

## Final Results and Future Improvements:
Results:
1. The R^2 for fama-french 4-factor model are higher than CAPM model, which describes the excess returns better.
2. For each of the banks, beta can be used to explain systematic risk. When beta is greater than 1, the bank stock price tends to be more volatile than the market. SMB, HML, and Momentum can also be good indicators about bank stock performance and profitability.

Improvements:
1. Some banks have missing value in Yahoo Finance. I will try to extract financial data from other external website to solve this problem.
2. To have a more direct understanding about parameters trend, it would be helpful to have a trend analysis. I plan to download a five-year financial data and develop a trend analysis for each paramaters through Tableau.
3. Based on 2, we can further optimize this model by bank categories. For example, four major bank categories can be Systemically-Important Financial Institutions (SIFIs) with assets over $50 billion, Super-Regional Banks with assets $10-$50 billion, Midsize Banks with assets $1-$10 billion, Community Banks with assets below $1 billion. We would be able to create a statistical descriptive analysis to deep into bank profitability by category.
4. Other than banking industries, we would be able to explore different industries, such as oil, infrastructure, technology to explore the stock volatility in different industries.
