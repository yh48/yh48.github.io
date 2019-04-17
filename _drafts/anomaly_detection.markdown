Anomaly detection problem for time series is usually formulated as finding outlier data points relative to some standard or usual signal.

**Additive outliers**: surprisingly large or small value occurring for a single observation. Subsequent observations are unaffected by an additive outlier.
Consecutive additive outliers are typically referred to additive outlier patches.

**Innovative outliers**: An innovational outlier is characterized by an initial impact with effects lingering over subsequent observations. The influence of the outliers may increase as time proceeds.

**Level Shift Outlier**: For a level shift, all observations appearing after the outlier move to a new level. In contrast to additive outliers, a level shift outlier affects many observations and has a permanent effect

**Transient Change Outlier**: Transient change outliers are similar to level shift outliers, but the effect of the outlier diminishes exponentially over the subsequent observations. Eventually, the series returns to its normal level.

**Seasonal Additive Outlier**: Appears as a surprisingly large or small value occurring repeatedly at regular intervals.

**Local Trend Outlier**: Yields a general drift in the series caused by a pattern in the outliers after the onset of the initial outlier.


Tsay (1988) proposed an iterative procedure for detecting mean level change to identify deterministic outliers


Two approaches: label each time point with anomaly / not anomaly,

forecast a signal for some point and test if this point value varies from the forecasted enough to deem it as an anomaly.

visualize a confidence interval, which will help a lot in understanding why an anomaly occurs and validate it.



### STL Decomposition

STL stands for seasonal-trend decomposition procedure based on Loess. split your time series signal into three parts:

seasonal, trend and residue.


if you analyze deviation of residue and introduce some threshold for it, you'll get an anomaly detection algorithm.

median absolute deviation to get a more robust detection of anomalies.

Twitter's Anomaly Detection library.

Generalized Extreme Student Deviation test to check if a residual point is an outlier.



https://github.com/twitter/AnomalyDetection

simplicity and robust it is.

rigidity regarding tweaking options (significance level).

One typical scenario in which is doesn't work well is when characteristics of your signal have changed dramatically.


### Classification and Regression Trees

First you can use supervised learning to teach trees to classify anomaly and non-anomaly data points.
- you need to have labeled anomaly data points.

To use unsupervised learning to teach CART to predict the next data point in your series and have some confidence interval or prediction error as in the case of the STL decomposition approach. You can check if your data point lies inside or outside the confidence interval using Generalized ESD test, or Grubbs' test.



### ARIMA

based on an approach that several points from the past generate a forecast of the next point with the addition of some random variable, which is usually white noise.


### Exponential Smoothing




[Grubbs's test for outliers](https://en.wikipedia.org/wiki/Grubbs%27s_test_for_outliers)

https://www.ibm.com/support/knowledgecenter/en/SS3RA7_15.0.0/com.ibm.spss.modeler.help/ts_outliers_overview.htm

https://blog.statsbot.co/time-series-anomaly-detection-algorithms-1cef5519aef2



[Package ‘tsoutliers’](https://cran.r-project.org/web/packages/tsoutliers/tsoutliers.pdf)


spike.





https://www.ibm.com/support/knowledgecenter/en/SS3RA7_15.0.0/com.ibm.spss.modeler.help/ts_outliers_overview.htm
