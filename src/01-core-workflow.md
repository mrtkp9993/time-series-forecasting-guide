# Core workflow

## Diagram

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

## Notes

* **Intermittent demand / many zeros**: This branch is for problems where the target series has a large number of zero values, which can pose challenges for traditional forecasting methods. Specialized techniques, such as Croston's method or intermittent demand forecasting models, may be more appropriate in this case.

* **Forecast combination / reconciliation**: This branch is for problems where multiple forecasting models are combined to produce a final forecast. This can be useful when different models capture different aspects of the data, or when there is uncertainty about which model is best. Forecast reconciliation involves ensuring that forecasts from different models are consistent with each other, especially when dealing with hierarchical or grouped time series data.
