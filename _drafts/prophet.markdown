

# Saturating Forecasts


By default, Prophet uses a linear model for forecast.
When forecasting growth, there is usually some maximum achievable point: total market size, total population size, etc.
This is called carrying capacity, and the forecast should saturate at this point.

-> Logistic growth trend model, with a specified carrying capacity.

cap must be specified for every row in the dataframe , and it does not have to be constant.


df['cap'] = 100
df['floor'] = 10

m.plot(forecast ,plot_cap = False)


# Trend Changepoints

Prophet detects changepoints by first specifying a large number of potential changepoints at which the rate is allowed to change.

# Seasonality, Holiday, effects, and regressors

If you have holidays or other recurring events that you'd like to model, you must create a dataframe for them. It has two columns (holiday and ds) and a row for each occurrence of the oliday.

it must include all occurrences of the holiday, both in the past and in the future.

You can also include columns lower_window and upper_window which extend the holiday out to [lower_window, upper_window] days around the date.
For instance, if you wanted to include Christmas Eve, in addition to Christmas you'd include low_window=-1. upper_window=0

## Built-in Country Holidays


Fourier Order for Seasonalities

Seasonalities are estimated using a partial Fourier sum.



## Uncertainty Intervals

- uncertainty in the trend
- uncertainty in the seasonality estimates
- additional observation noise.

Default is 80%

forecast = Prophet(interval_width=0.95).fit(df).predict(future)

To track the uncertainty in seasonality, need Bayesian sampling by specifying mcmc_samples.

mcmc_samples=300



Non-Daily data and diagnostics







https://peerj.com/preprints/3190/

https://en.wikipedia.org/wiki/Fourier_series#/media/File:Fourier_Series.svg
