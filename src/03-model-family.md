# Model family selection

## Table

| Model family condition | Candidate models                                                                             |
| ---------------------- | ----------------------------------------------------                                         |
| Stationary linear      | AR / MA / ARMA                                                                               |
| Trend / nonstationary  | ARIMA                                                                                        |
| Seasonal               | SARIMA / ETS                                                                                 |
| Multiple seasonality   | TBATS / MSTL                                                                                 |
| Exogenous inputs       | ARDL / ARIMAX                                                                                |
| Multivariate           | VAR / VECM                                                                                   |
| Changing variance      | ARCH / GARCH / stochastic volatility / Generalized Autoregressive Score (GAS)                |
| Long memory            | ARFIMA / FIGARCH                                                                             |
| Nonlinear / regime switching | TAR / SETAR / STAR / Markov switching                                                  |
| Nonlinear ML           | Neural network autoregression (NNAR)                                                         |
| Latent components      | State-space / structural time series / Kalman filter                                         |
| Mixed frequency        | MIDAS                                                                                        |
| Intermittent demand    | Croston's method / TSB                                                                       |

## Notes

* Benchmarks always included: mean, naive, drift, seasonal naive

* Validation: expanding or rolling window time-series cross-validation

* Evaluation: MAE, RMSE, MASE, sMAPE, interval coverage where relevant
