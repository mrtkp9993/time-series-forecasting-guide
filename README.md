# Time Series Forecasting Workflow

## Core Workflow

```mermaid
flowchart TD
    A[Define problem] --> D[Initial EDA]
    D --> E{Problem structure?}

    E -->|One target series| F[Univariate branch]
    E -->|Multiple target series| G[Multivariate branch]
    E -->|One target with exogenous inputs| H[Dynamic regression branch]

    F --> K[Fit benchmarks and candidates]
    G --> K
    H --> K

    K --> L[Residual and stability diagnostics]
    L --> M{Diagnostics adequate?}

    M -->|No| N[Respecify model]
    N --> K

    M -->|Yes| O[Time-series cross-validation]
    O --> P[Forecast evaluation]
    P --> Q{Best parsimonious model?}

    Q -->|No| K
    Q -->|Yes| S[Finalize forecast]
```

## Diagnostics & Model Selection

```mermaid
flowchart TD
    B{Problem structure}

    %% Univariate
    B --> |Univariate| U1[Trend and stationarity]
    U1 --> U2[Seasonality checks]
    U2 --> U3[Variance diagnostics]
    U3 --> U4[Breaks and interventions]
    U4 --> U5[Special dependence checks]
    U5 --> Z[Candidate model list]

    %% Multivariate
    B -->|Multivariate| M0[System diagnostics]
    M0 --> M1{Integrated?}
    M1 -->|No| M2[VAR]
    M1 -->|Yes| M3[Cointegration tests]
    M3 --> M4{Cointegrated?}
    M4 -->|Yes| M5[VECM]
    M4 -->|No| M2[VAR in differences / differenced VAR]
    M2 --> Z
    M5 --> Z

    %% Dynamic regression
    B -->|Exogenous inputs| X0[Input-output diagnostics]
    X0 --> X3{Regression form}
    X3 -->|Lagged regressors| X4[ARDL / UECM / ECM]
    X3 -->|Regression with ARMA errors / ARIMAX| X5[ARIMAX / dynamic regression]
    X4 --> Z
    X5 --> Z
```

## Model family selection

| Condition              | Candidate models                                     |
| ---------------------- | ---------------------------------------------------- |
| Stationary linear      | AR / MA / ARMA                                       |
| Trend / nonstationary  | ARIMA                                                |
| Seasonal               | SARIMA / ETS                                         |
| Exogenous inputs       | ARDL / ARIMAX                                        |
| Multivariate           | VAR / VECM                                           |
| Changing variance      | ARCH / GARCH / stochastic volatility                 |
| Long memory            | ARFIMA / FIGARCH                                     |
| Nonlinear / regime     | TAR / SETAR / STAR / Markov switching                |
| Latent components      | State-space / structural time series / Kalman filter |

## Contact

[Murat Koptur](https://www.linkedin.com/in/muratkoptur/)
