# Unit 10—A Yen for the Future

![Yen Photo](Images/unit-10-readme-photo.png)

## Background

The financial departments of large companies often deal with foreign currency transactions while doing international business. As a result, they are always looking for anything that can help them better understand the future direction and risk of various currencies. Hedge funds, too, are keenly interested in anything that will give them a consistent edge in predicting currency movements.


## Time-Series Forecasting

The first part of the analysis, provided by the `time_series_analysis.ipynb` notebook, contains code to model the short-term price movement of the Yen with respect to the U.S. Dollar.

The Hodrick-Prescott Filter is used to extract noise data and isolate the daily returns. Price modeling is performed using the ARMA and ARIMA models. Lastly, volatility is modeled with GARCH.

### Conclusions

A slight edge is given to the ARMA model since AIC and BIC (15798.142, 15832.765 respectively) are smaller than those for ARIMA, and the prediction continues the existing short-term historical trend. However the ARIMA model has a better fit with 0.302, as opposed to 0.422.

Based on the disagreement of two models (ARMA and ARIMA) that the price of Yen is forecast to either go up or down in the short term, I would not recommend buying the Yen at this time as we do not have a reliable conclusion.

The risk of Yen is expected to increase based on the GARCH analysis.

Based on the model fit assessment, I would not feel confident using these models for trading that requires directional prediction. One mitigating factor could be good prediction history if the models are tested against historical data. However, for trading based on volatility these models predict an increase in volatility.

- - -

## Linear Regression Forecasting

In the second part of the analysis, in notebook `regression_analysis.ipynb`, the Scikit-Learn linear regression model to predict Yen futures returns with *lagged* Yen futures returns and categorical calendar seasonal effects.

After splitting the returns and lagged returns into training and testing data, a sklearn linear regression model is fit. Predictions are compared with known test data and the model performance is evaluated.

The following performance metrics were computed:

| Metric | In-Sample | Out-of-Sample |
| - | - | - |
| Mean Squared Error (MSE) | 0.02626851739283526 | 0.028607388052668496 |
| Root Mean Squared Error (RMSE) | 0.1620756533006585 | 0.16913718707802994 |

### Conclusions

The Scikit-Learn linear regression model performs with similar error metrics in both the in- and out-of-sample datasets. In-sample has a slightly better MSE, and out-of-sample a very slightly better RMSE. Performance can be considered "consistent" across both datasets.

MSE and RMSE are similar between in- and out-of-sample performance. This leads to the conclusion that the model makes predictions with similar accuracy for both the trained and test data.

MSE and RMSE values are favorable (MSE < .05), indicating that the model is accurate.
