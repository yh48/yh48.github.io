Fitting a bayesian structural time series model to observed data which is later used for predicting what the results would be had no intervention happened in a given time period.

Use the predictions of the fitted model, as a reference to what probably would had been observed with no intervention taking place.

Bayesian Structural Time Series models:

$y_t = Z^T_t\alpha_t + \beta X_t + G_t\epsilon_t$

$a_{t+1} = T_t\alpha_t + H_t\eta_t$

$\epsilon_t \sim \mathcal{N}(0, \sigma_t^2)$

$\eta_t \sim \mathcal{N}(0, Q_t)$

$a$ : state of the series
$y_tt$: linear combination of the states plus a linear regression with the covariates $X$.

$\epsilon$ measurement noise

By varying the matricex $Z$, $T$, $G$, $H$ we can model several distinct behaviors for the time series.

random walk component
