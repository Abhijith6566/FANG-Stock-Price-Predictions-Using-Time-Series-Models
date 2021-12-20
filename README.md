# FANG-Stock-Price-Predictions-Using-Time-Series-Models

# Introduction

Stock markets are very volatile, but volatility is reflected among common group of stocks. 
Tech giants Facebook, Apple , Amazon and Google are similar type of companies and stocks . Their volatility is only dependent on their own movements?
The idea here is ,If they are closely related , optimistic or pessimist news might have similar effect on their stock price movement.
This project is preliminary idea , for achieving much more accuracy many more companies should be considered like Microsoft, Apple etc.. 

# Data Preparation

Downloaded Individual CSV files for each stock ; Amazon, FB, Netflix and google.
Set date as an Index for these data sets.
Joined data sets on date column; so that data is available from 2012-05-18 to 2019-08-23 as fb is listed on stock market only from 2012 -05.

![image](https://user-images.githubusercontent.com/86455496/146805100-f2181441-e025-4f86-8203-26fb819769e8.png)

# Stationarity

Checked stationarity of data with ADF test
Checked with ACF and PACF plots
All four stock prices are I(1) process, they are not stationary. For our analysis we will need to convert series to stationary
So, I have made first difference each stock in FANG


# Models

> BASE model ( Naïve model, Yt=B*Yt-1 + Error)
> SARIMAX
> Vector error correction model


# SARIMAX

SARIMAX =Updated ARIMA modelling including seasonal effects and exogenous factors.
Checked for various combinations, it seems 
Lags of FB are not helpful for prediction of FB
(by looking at p-values)
Similarly, For other stocks in FANG it is same,
Except for Google.


# Granger Causality and Johansen's cointegration

Granger causality will help us to know causation effect among variables, the only problem with this technique is only 2 variables can be taken at a time. 
As we can see for number of lags 3 Netflix have causal effect on amazon.
Similarly,  FB predict amazon, fb predict google and amazon predict Netflix. 

Checking for cointegration is crucial for building a VECM model. If there is are no cointegration vectors in feature matrix, It is always suggested to use vector auto regressive process.  ( Where it is assumed that there is no correlation among lags of variables in the model)
Used Johansen’s cointegration, which is helpful in predicting cointegrated vector ( Number of Cointegrated vectors is equal to number of relationship among the variables) 
It can be used either with Eigen values or Trace statistic


# Model Performance 

>Mean absolute Percentage error as comparison metrics
> For the base model , MAPE is on average 1.30
MAPE for VECM is on average 0.30, so the error have been reduced four fold, we can suggest this model with some more tweaks and it can be used for predictions with a very minimal error








