# Diagnostics & Model Selection

## Diagram

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

## Notes

* Trend and stationarity: ADF, PP, KPSS, break-point unit-root tests

* Seasonality: seasonal dummies, seasonal plots, seasonal unit-root tests

* Variance: log/Box-Cox, ARCH-LM, squared residual checks

* Breaks and interventions: Chow, Zivot-Andrews, Bai-Perron, intervention dummies

* Special dependence: long memory, threshold effects, regime changes, nonlinear dynamics

* Input-output diagnostics: lag inspection, prewhitened Cross-Correlation Function (CCF), intervention and transfer effects
