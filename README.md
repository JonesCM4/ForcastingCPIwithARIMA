<h1>Consumer Price Index Forecast using an Auto Regressive Integrated Moving Average (ARIMA) Model</h1>
<h2>Overview</h2>
The goal of this analysis is to adequately model and forecast CPI using an ARIMA model. CPI is often used as a proxy for inflation and is an important economic indicator used to assess the state of the macro economy. The CPI data is retrieved using the Federal Reserve Bank's API. To reproduce this analysis, replace the 'key' variable with your own API key. API keys are obtained through the Federal Reserve Bank of St. Louis' official website: https://fred.stlouisfed.org/docs/api/fred/.

<h2>Federal Reserve and DSGE Models</h2>
The Federal Reserve typically uses Dynamic Stochastic General Equilibrium (DSGE) models to forecast the macroeconomy, including CPI. These models are advantageous because they allow economists to tweak parameters in one area of the economy and observe how these changes directly or indirectly affect CPI. DSGE models incorporate a broad set of economic factors, making them highly valuable for policy analysis and long-term forecasting. When considering whether an ARIMA model is appropriate for forecasting CPI, it's important to take into account the Federal Reserve's reliance on DSGE models. DSGE models incorporate various aspects of the economy, capturing the complex interactions that directly or indirectly affect CPI, which can influence the forecast differently than an ARIMA model might. DSGE models allow for a comprehensive approach to macroeconomic forecasting. In contrast, ARIMA models are simpler. ARIMA models are effective for short-term forecasting when the extraneous macroeconomic variables influencing CPI are assumed to remain relatively constant and when the assumptions of stationarity of the mean and variance are met. However, the differences in how DSGE and ARIMA models handle these variables may lead to different forecasting outcomes.

<h2>Differencing Approach</h2>
A line chart of the CPI data reveals an obvious upward trend over time. This trend violates the assumption of consistency in means for any two similar lengths of time. In other words, the data is not stationary. To control for the violation of consistency of means, a first-order differencing approach is applied. The differenced data is then examined with a graph of the rolling mean and standard deviation which is shown to be relatively flat, suggesting that first-order differencing adequately accounts for the inconsistency in means.

![Screenshot 2024-08-06 145922](https://github.com/user-attachments/assets/84c4077a-fa46-4e3c-8a4f-4d6df726cafe)

<h2>Stationarity Testing and Model Selection</h2>
An Augmented Dickey-Fuller (ADF) test is conducted to quantitatively assess stationarity. A p-value of 0.002 indicates statistical significance, leading to the rejection of the null hypothesis that the time series has a unit root (i.e., it is non-stationary). The ACF and PACF plots are utilized to determine the appropriate number of autoregressive terms (p) and moving average terms (q) for the ARIMA model, and the first-order differencing (d=1) is applied. Finally, an ARIMA(12, 1, 1) model is applied. It is important to note that python will automatically integrate the differenced forecasts back into the original scale upon output.

![Screenshot 2024-08-05 084321](https://github.com/user-attachments/assets/87e89b15-3917-455a-9ba7-fd26fcb80f9f)

<h2>Model Evaluation</h2>
The lowest Akaike Information Criterion (AIC) value achieved in this analysis was 763.681. Further, a Mean Average Percentage Error (MAPE) of 0.13% was achieved when backtesting the data from July 2022 to July 2024, indicating highly accurate forecasts. The ARIMA model successfully accounts for the trend and seasonality in the CPI data. While DSGE models offer a more comprehensive approach to forecasting the macroeconomy, including CPI, ARIMA analysis remains a valuable tool, especially when extraneous variables are assumed to remain relatively constant and the assumptions of stationarity are met.

![ARIMA Forecast](https://github.com/user-attachments/assets/abbc5c4e-d14e-4b43-b6f3-ad873dd5d8ec)

