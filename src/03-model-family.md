# Model family selection

## Table

| Model family condition | Candidate models                                     |
| ---------------------- | ---------------------------------------------------- |
| Stationary linear      | AR / MA / ARMA                                       |
| Trend / nonstationary  | ARIMA                                                |
| Seasonal               | SARIMA / ETS                                         |
| Exogenous inputs       | ARDL / ARIMAX /            MIDAS                     |
| Multivariate           | VAR / VECM                                           |
| Changing variance      | ARCH / GARCH / stochastic volatility                 |
| Long memory            | ARFIMA / FIGARCH                                     |
| Nonlinear / regime     | TAR / SETAR / STAR / Markov switching                |
| Latent components      | State-space / structural time series / Kalman filter |

## Notes

* Benchmarks always included: mean, naive, drift, seasonal naive

* Validation: expanding or rolling window time-series cross-validation

* Evaluation: MAE, RMSE, MASE, sMAPE, interval coverage where relevant