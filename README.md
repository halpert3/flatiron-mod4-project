# Overview

Made for a Flatiron School data science course, the purpose of this project was to find areas of potential investment for investors in housing real estate markets. 

There are four Jupyter notebooks in this repository:

1. EDA, for Exploratory Data Analysis
2. checking_trends, to examine data and see if data could be made stationary
3. modeling, to experiment with various time series model types and parameters
4. forecasting, to predict housing prices for the best-performing models 

# Data

This project uses time series data from Zillow, an online real estate marketplace. 

- Almost 15,000 zip codes in dataset. About 35% of all zip codes in United States.
  - Data set consists of mean housing prices for each zip code, April 1996 - April 2018
- For this project, I looked at zip codes in the New Orleans area to investigate and model
  - Ended up using five zip codes

# Process

## Checking Data for Stationarity

- Time series models only work if data is already or can be made stationary
  - Meaning the mean, variance and autocorrelation structure do not change over time. 
- Used **Dickey-Fuller Test** to check various data manipulation strategies
  - Root Transformations (didn’t pass)
  - Rolling Mean Subtraction (passed)
  - Differencing (passed)

Went with differencing as it works well with ARIMA models



## Modeling

### Process

#### Found ARMA Baseline

Ran ARMA on each zip code with minimum differencing *d* and tried various (*p, q*) parameters to get an idea of minimum AIC 

#### Performed Train-Test Split 

Made training set all data except for final 12 months which were reserved as test data

#### Ran ARIMA models

For some zip codes, experimented with ARIMA and *for* loops of various (*p, d, q*) parameters on training data

#### Ran auto-ARIMA models

Let the module automatically find which parameters yielded lowest AIC on training data. In the end, went with best auto-ARIMA parameters for all five zip codes

#### Re-ran parameters on SARIMAX models

SARIMAX offers diagnostic and forecasting functionality 

### Model Assessment

To choose the best models that would yield the most predictable forecasts, I compared the AIC metric and root mean squared errors (between forecasted training data and reserved test data). 

## Forecasting

I ultimately chose the time series models of three zip codes to run on the full datasets for forecasting. 

- Two zip codes were  predicted to yield low ROIs (neither higher than 1.4%) with relatively low risk
- The third zip code was predicted to fall sharply and was a high risk investment

# Conclusion and Next Steps

None of the five zip codes could be recommended as good investment opportunities. Nevertheless, as a student working through this project, my knowledge of time series models was deepened. 

Possible next steps were this project to continue:

- Experiment with other types of time series modeling like Facebook Prophet to see if they yielded different results

- Investigate other zip codes for investment opportunities for this hypothetical client 