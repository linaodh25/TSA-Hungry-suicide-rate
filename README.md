# Suicide Rate in Hungary (1955–2023): Time Series Analysis

**TSA Project — OUADAH Lina Selma**

## Overview
This project applies Time Series Analysis (TSA) to 69 years of WHO data on Hungary's 
suicide rate, which rose to one of the highest in the world (~46/100k in 1983) before 
falling by over 50% by 2019. The goal: test whether a statistical model can capture 
and forecast this trend.

## Process
1. **Visual Inspection** – identified a non-stationary series with a clear trend and 
   two structural breaks (1989, 2004).
2. **Box-Cox** – confirmed no variance transformation needed.
3. **Stationarity Tests** – trend test + ADF confirmed non-stationarity → differencing required.
4. **Differencing (d=1)** – selected as optimal order via ACF analysis.
5. **ACF/PACF** – pointed to an AR(2)-dominant structure.
6. **Model Fitting** – compared ARIMA(1,1,0), (2,1,0), (1,1,1), (1,1,2), (2,1,1) using 
   AIC/BIC and residual diagnostics (Shapiro-Wilk, Runs test, Ljung-Box).
7. **Forecasting** – **ARIMA(2,1,1)** selected as final model (RMSE = 1.585, MAPE = 11.85%), 
   with all holdout values inside the 95% CI.

## Key Findings
- Structural breaks (1989 fall of communism, 2004 EU accession) limit ARIMA's 
  constant-dynamics assumption, causing slight underestimation.
- Despite the COVID-19 shock (2020–2021), actual values stayed within the prediction 
  interval — a sign of well-calibrated uncertainty bounds.

## Files
- `SuicideRate_Hungary_1955_2023_TSA.ipynb` — full analysis notebook
- `SuicideRate_Hungary_1955_2023_TSA.pdf` — report/export version
- `suicide-rate-who-mdb.csv` — WHO source data

## Tools
R
