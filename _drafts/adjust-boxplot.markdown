「論文読み」（可視化と異常値検知）An Adjusted Boxplot for Skewed Distributions

# 要約

この[論文](https://wis.kuleuven.be/stat/robust/papers/2008/adjboxplot-revision.pdf)に基づいて、2008年提唱した、AdjustedBoxplotの要点をメモします。

Adjusted　Boxplotというのは、従来存在した、一次元データ可視化箱ひげ図（Boxplot）の改善です。特に、歪みを持ってるデータに対して、異常値の判断の改善があります。

# 背景

## 箱ひげ図とは？

一次元のデータセット$X_n{x_1,x_2,...,x_n}$に対して、箱ひげ図は下記の５つの統計量を表示する図です：

- 中央値：Q2
- 第1四分位点: Q1
- 第3四分位点: Q3
- 最小値： Q1 - 1.5IQR
- 最大値： Q3 + 1.5IQR

箱ひげ図の描き方は：

- 中央値を


## 箱ひげ図の利点は？

５つの統計量が持っているので、頑健な可視化ツールである。

異常値検知


## 箱ひげ図の欠点は？

箱ひげ図は頑健かつ便利なツールですが、考えずに使えば、問題発生する可能性も存在します。一つの問題は：判定された異常値は、本当に異常値なのか？


以下のケースを考えます：

1. 裾の重い分布
2. 歪みを持ち分布

異常値の判定は適切かどうか、実際のケースによるけど、二つの分布を研究して、判定されたデータの量を調べます：

以下の分布を従って、乱数10万ずつ作成して、外れ値のパーセンテージを調べます：

分布 | 中央値 | 外れ値比率（下） | 外れ値比率（上）
----|----|-------|-------
標準正規分布  | 0.0027  | 0.334%	  |  0.322%
標準T分布（自由度２） | -0.0020  | 4.05%  |  4.09%
カイ二乗分布（自由度２） |  1.387 | 0%  |  4.83%

T分布は、正規分布より、裾が重い分布、
カイ二乗分布は、裾が重いかつは歪みを持ちの分布です。
より多くのデータは、異常値に判定された。

# 改善：Adjusted Boxplot で解決

一つの説明は、Adjusted Boxplotは、異常値検知の完璧なソリューションではありません。（そもそも、異常値検知の完璧なソリューションが存在するかとうか、わからない）

解決方法は、Q_1 - 1.5 IQRのところに、適当なパラメータを追加します。



$$
[Q_1 - 1.5 e^{-4MC}IQR, Q_3 +1.5e^{3MC}IQR]
$$

$$
[Q_1 - 1.5 e^{-3MC}IQR, Q_3 +1.5e^{4MC}IQR]
$$


### Thick tail







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
