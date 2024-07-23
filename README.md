# ARMA Model Analysis for Stock Price Data

This project implements and analyzes an Autoregressive Moving Average (ARMA) model on stock price data using R. The analysis is conducted using Apple Inc.'s (AAPL) stock data obtained from Yahoo Finance.

## ARMA Model Overview

The Autoregressive Moving Average (ARMA) model combines both autoregressive (AR) and moving average (MA) components to capture temporal dependencies in a time series. It is expressed as:

$$ x[t] = c + \sum_{i=1}^p \phi_i x[t-i] + \sum_{j=1}^q \theta_j \epsilon[t-j] + \epsilon[t] $$

where:
- $x[t]$ is the time series
- $c$ is a constant
- $\phi_i$ are the parameters of the AR model
- $\theta_j$ are the parameters of the MA model
- $\epsilon[t]$ are white noise error terms
- $p$ is the order of the AR model
- $q$ is the order of the MA model

## Implementation

The implementation is carried out in R, using the following steps:

1. **Data Acquisition**: Apple Inc. stock data is fetched using the `quantmod` package.
2. **Data Transformation**: Log returns of the adjusted closing prices are computed.
3. **Model Selection**: An iterative process is used to select the best ARMA(p,q) model based on AIC.
4. **Model Fitting**: The selected ARMA model is fitted to the log returns.
5. **Residual Analysis**: Residuals from the ARMA model are analyzed using ACF and Ljung-Box test.

## Results

- **Data Preprocessing**: Log returns of AAPL stock prices are computed and analyzed.
- **Model Selection**: The best ARMA model is selected based on the lowest AIC value.
- **Model Fit**: The selected ARMA model is fitted to the log returns.
- **Residuals Analysis**: 
  - ACF of residuals is plotted and examined.The residuals are close to being white noise (uncorrelated), but not perfectly so model is adequate but could   
    potentially be refined further to capture any remaining subtle patterns in the data.
  - Ljung-Box test is performed on the residuals.
  - Ljung-Box test results: X-squared = 50.145, df = 20, p-value = 0.0002111
    ![image](https://github.com/user-attachments/assets/5e9fe718-2a1f-4f62-ae43-c7260ba28e8b)


## Conclusion

The analysis shows that the selected ARMA model may not fully capture the underlying dynamics of the data. The low p-value (0.0002111) in the Ljung-Box test suggests that we can reject the null hypothesis of independence in the residuals. This indicates that there might be some remaining autocorrelation in the residuals, and the model could potentially be improved.

## Future Work

1. Consider ARIMA models to account for potential non-stationarity.
2. Explore more advanced time series models like GARCH for volatility modeling.

## Files

- `1.R`: The R script containing the implementation of the ARMA model selection, fitting, and residual analysis.

## Dependencies

- R
- quantmod package
