

https://wis.kuleuven.be/stat/robust/papers/2008/adjboxplot-revision.pdf


**boxplot**: univariate data set analysis

- putting a line at the height of the sample median Q2
- drawing a box from te first quartile Q1 to the third quartile Q3. The length of this box equals the interquartile range IQR = Q3-Q1, which is a robust measure of scale
- classifying all points outside the interval (the fence)

[Q1 - 1.5 IQR, Q3+1.5IQR]
as potential outliers and marking them on the plot

- drawing the whiskers as the lines that go from the ends of the box to the most remote points within the fence.


**Problem**:

observations outside the fence are not necessarily 'real' outliers that behave different from the majority of the data.

Thick tailed symmetric distributions: many regular observations will exceed the outlier cutoff values defined in (1)

**Solution**

- Propose an adjustment to the boxplot that can be applied to all distributions
- Estimate the underlying skewness with a robust measure, to avoid masking the real outliers


Skewness adjustment to the boxplot

measure the skewness of a univariate sample {x_1,..., x_n} from a continuous unimodal distribution F, we use medcouple (MC):

MC = med h(x_i, x_j)

$$h(x_i, x_j) = \frac{(x_j - Q_2)-(Q_2 - x_i)}{x_j - x_i}$$

Medcouple always lies between -1 and 1,

a distribution that is skewed to the right has a positive value for the medcouple,

skewed to the left has a negative value for the medcouple.

a symmetric distribution has a zero medcouple.

robust measure of skewness has a bounded influence function and a breakdown value of 25%, at least 25% outliers are needed to obtain a medcouple of +1 (or -1)

Introduce some function h_l(MC) and h_u(MC) into the outlier cutoff values.


$$
[Q1-h_l(MC)IQR, Q_3+h_u(MC)IQR]
$$

and ensure:

h_l(0)=h_u(0)=1.5


$$
[Q_1 - 1.5 e^{-4MC}IQR, Q_3 +1.5e^{3MC}IQR]
$$

$$
[Q_1 - 1.5 e^{-3MC}IQR, Q_3 +1.5e^{4MC}IQR]
$$
