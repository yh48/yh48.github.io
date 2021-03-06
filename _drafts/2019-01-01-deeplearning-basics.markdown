---
layout: post
title:  "深層学習勉強メモ：（１）ニューラルネットワーク"
date:   2019-01-01 21:00:00 +0900
categories: deeplearning
---

* content
{:toc}


自分の理解ために、深層学習の基礎概念からもう一回勉強して、自分の認識によりメモします。私の認識の限りを書いたから、齟齬のところがあります。

内容が膨大のため、記事を分けて書きます。

本文は、深層学習の基礎、ニューラルネットワークのみ紹介します。

# 要約

本文の内容簡単にまとめます：

まずは、深層学習とニューラルネットワークの概念を紹介します。

さらに、ニューラルネットワーク学習と予測の原理とテクニクを紹介します。

最後に、ニューラルネットワークの実装の概念を紹介します。

# 深層学習とニューラルネットワークと機械学習

実際は、深層学習は新しい概念ではない。

深層学習またディープラーニングとは、多層のニューラルネットワークによる機械学習手法である。

なので、深層学習勉強するために、機械学習とニューラルネットワークの知識は前提です。深層学習勉強するために機械学習の最低限知識をまとめます。

# ニューラルネットワーク

## 構造

ニューラルネットワークとは、多層パーセプトロンです（下図）。

予測する時に、データは一番左側から、右に行きます。出力は予測の結果である。

複数の層を用いた構造です。
一番左の層は、入力層です、
一番右の層は、出力層です。
その間の全て層は、隠れ層と呼びます。

各層は、ニューラルという計算単元をます。

各層は、全連結と呼びます。

ニューラルはなにものですか？数値を受け取り、数値を出力する計算単元です。普段は、以下の構造を持っています：




なぜかというと、パーセプトロンから紹介しなければならない。

**パーセプトロン**　複数の信号を入力として受け取り、一つの信号を出力するのアルゴリズムです。
信号というものは、0,1の二値の値です。

例えば、論理回路のAND関数は、パーセプトロンです：

XORゲートを表示するときに、パーセプトロンが表示できない。
既存ゲートを組み合わせて、多層パーセプトロンを構築して、表示できます。

理論上2層のパーセプトロンであれば、コンピュータを作ることができる。

2層のパーセプトロン（活性化関数に非線形なシグモイド関数を用いたもの）を用いれば、任意の関数を表現可能であることが証明されています。

層が幾重にも重なった構造として作られるのが自然な流れです。

MLP(MultiLayerPr)





### 活性化関数

活性化関数は必ず非線形が必要です。

**活性化関数**：　入力関数の和を出力に変換する関数。

代表的な活性化函数は：

- シグモイド（Sigmoid）函数
- ステップ函数
- ReLU函数

シグモイド函数はクラシカルの活性化関数だけど、ReLU函数シンプルなので、計算も速い、深層学習の時よく使ってる函数です。



### 入力と出力

機械学習の二つクラシカルのタスクは：

- 分類
- 回帰

#### 問題解決への出力

どうやて入力から、欲しい出力を変換するのか、これは、出力層解決すべき問題です。

一般的に、出力層の活性化関数を変更して、欲しい結果を出力できます。

### 分類問題：ソフトマックス（Softmax)関数

多クラス分類を行う時に、出力層はSoftmax函数をよく使っています。

Softmax函数は下記のかたちで：

$$
y_k = \frac{exp(a_k)}{\sum_{i=1}^{n}exp(a_i)}
$$

実は簡単です：各クラスの「確率」として解釈しています。

出力層は、ニューラルの数は、分類と同じ。一つのニューラルのアウトプットは、各分類に対して、確率である。

一番大きいニューラル一番可能性高い。

### 回帰問題：恒等関数

入力のまま、何もしたいて出力します。


出力層は、実際に様々な関数は使えます。

例えば、深層学習で、POS（NLP固有表現抽出など）する時に、CRF（ConditionalRandomField）はよく使っています。


## 学習と予測


今まで、ニューラルネットワークが任意の関数を表現可能であることがわかりましたが、どうやて、適当なパラメタを配置するのか、今から議論する内容です。


入力から出力への変換は既にわかるので、どうやて変換するのかを解決したいと思います。

### 機械学習のプロセスを理解します

X, y
教師あり機械学習の場合は：

二つの段階があります：

- 学習
- 予測

学習段階は、既存のFeatureとレベルを使って
関数の各最適化パラメタを求めることです。


学習段階は、Labelが付けたデータから、最適なパラメーターを探す。
予測段階は、最適なパラメータを使って、Labelが付けってないデータから、Labelを予測します。


**最適化** とは、既存データから見ると、誤差や、損失は一番小さいパラメタです。

誤差、損失は、定義した損失関数（LossFunction）など表現します。

予測プロセスは、ただ学習段階求めたパラメタと予測したいFeatureを使って、レベルを付けるプロセスです。

以上の概念はニューラルネットワークも適用です。

### 予測のプロセス

仮に、各ニューラルのパラメタは既にわかった場合、予測はただ、入力からの計算だけです。

データフローは、入力から、各層ニューラルに従って、出力を計算します。

このプロセスはFeedforwardと呼びます。

### 学習のプロセス

最適化は、損失関数を

まず、損失関数を定義します。

認識精度が高くなるようなパラメータを獲得したいので、

出来るだけ、小さな損失関数の場所を探すために、パラメータの微分を計算し、その微分の値を手掛かりにパラメータの値を徐々に更新して行きます。

精度　→　微小な変化は反応されず、しかも連続です。

**損失関数（LossFunction）**

多クラス分類を行う時に、**交差エントロピー誤差**　を用いる場合が多くあります。

一つのデータに対して、誤差関数は：
$$
E=-\sum_kt_k\log y_k
$$

t_kはラベルのOneHotEncodingです（正解のみ１その他の値は０）。例えば、3分類、2つめのデータは正解の場合は：

$$t_k = (0,1,0)$$

全体に対して、損失函数はすべてのデータの誤差関数の合計です：

$$L=-\frac{1}{N}\sum_n\sum_kt_{nk}\log y_{nk}$$

今まで、毎回Feedforwardのあとは、損失関数の計算はできます。


さらに、損失関数の手法を紹介します。

損失関数は複雑なので、

**勾配降下法Gradient Descent**　というアルゴリズムを使っています。

全ての変数の偏微分をベクトルとしてまとめたものは勾配（gradient）である。


勾配の方向が必ず最小値を指すとは限らないにせよ、その方向に進むことで関数の値を最も貼らせることができます。

$\sigma$ 学習率と呼ばれます。

その勾配に学習率を掛けた値で更新する処理をStepNumで指定された回数を繰り返します。


しかし、こういう計算が、実装が簡単ですが、コストがかかります。

重みパラメータんの勾配の計算を効率よく行う手法である、誤差逆伝播です。

計算グラフ


連鎖率を存在するため、誤差逆伝播の計算は可能になります。


簡単にいうと、


訓練データとテストデータを分けて

微分、x少し変更発生したら、yの変化率でいうものです。

### 実装する問題

**ミニバッチ学習**：

**確率的勾配降下法Stochastic Gradient Descent**:

実装する時に、トレニングデータは何百万件、何億件の場合もありますから、すべてのデータを対象にして、損失関数を求めるには、現実的ではありません。

このため、ミニバッチ学習を使っています。

実装する時に、2の, 32,64,256はよく使っています。


以上は、ニューラルネットワークの学習と予測の全ての問題を解答したと思います。

深層学習の実装するときブロセスから振り返します。



学習のプロセス（斎藤さんの本により）：

- Step-1 ミニバッチ
  - 訓練データの中からランダムに複数のデータを選ぶ出す
- Step-2 勾配の算出
  - 誤差逆伝播法により、各重みパラメータに関する損失関数の勾配を求める
- Step-3　パラメータの更新
  - 勾配を使って重みパラメータを更新する
- Step-4　繰り返す
  - Step-1, Step-2, Step-3 を必要な回数だけ繰り返す


要点を振り返します：

最適なパラメータを見つけるのプロセスです。

学習段階のポイントは以下です：

- 学習の目標：**損失関数** 最小化
- 学習手法：**誤差の逆伝播（Backpropagation）**
- 手法理論：**合成関数の微分の法則（チェインルール）** と　**勾配降下法**
- 実装する時に、ほぼ **ミニバッチ** のSGDを使っています


###　ニューラルネットワークの予測と学習

#### 予測のプロセス

線形関数と活性関数を使ってるニューラルネットワークは、シンプルそうだけど、表現力は意外に強い。
なぜかでいうと、名詞部分の[パーセプトロン]()に参考します。



#### 学習のプロセス



**Neurons**

**Sigmoid Neurons**

> In fact, a small change in the weights or bias of any single perceptron in the network can sometimes cause the output of that perceptron to completely flip

Sigmoid Neuronを導入して、この問題を解決します。

$$
\rho(z) = \frac{1}{1+e^{z}}
$$




**バッチ学習**：




**多層ニューラルネットワークの構造**：

- 入力層
- 隠れ層
- 出力層

(Sometimes it is called multilayer perceptrons or MLPs, due to historical　reason, though the neurons are sigmoid neurons)

## ニューラルネットワークの実装

実装のため、深層学習理解して上で、最低限の知識は：

**Numpy**　の基本知識（多次元配列の計算など）。

Numpyについては、別途にまとめます。


### Iris 多クラス分類

Source Codeは[こちら]()に確認してください。

### Handwritten digits 多クラス分類

Source Codeは[こちら]()に確認してください。

# 名詞


**パーセプトロン Perceptron**: ニューラルネットワークの起源です。

パーセプトロンというアルゴリズムは、

入力：(x1, x2, ...)、複数のバイナリー値
出力：y、一つの二値の値です。

$$
y= 0 (w_1x_1+w_2x_2 \leq \theta)
1 (w_1x_1+w_2x_2 \geq \theta)\
$$

論理回路の場合：

多層パーセプトロン


コンピュータの計算は、実は、NANDゲートの組み合わせだけです。


takes several binary inputs, x1,x2,…, and produces a single binary output:

[wikipedia](https://ja.wikipedia.org/wiki/%E3%83%91%E3%83%BC%E3%82%BB%E3%83%97%E3%83%88%E3%83%AD%E3%83%B3)

**シグモイド関数 sigmoid function**

[wikipedia](https://ja.wikipedia.org/wiki/%E3%82%B7%E3%82%B0%E3%83%A2%E3%82%A4%E3%83%89%E9%96%A2%E6%95%B0)



# 振返り


簡単にいうと：

深層学習とは、多層（4層以上）のニューラルネットワークを用いて、機械学習の手法である。

ニューラルネットワークは、層を持っています。

各層は、複数のニューラルを持っています。

ニューラルは、様々の計算を持っています（普通は、計算と活性化関数です）。

以上は、深層学習の基本構造です。

予測は、各Featureは、入力層から、の計算です。

学習は、損失関数最小化に目標して、勾配降下法を用いて、最適化のパラメータを探すことです。




# References

**[1]ゼロから作るDeepLearning**, 斎藤康毅, [Book](https://books.rakuten.co.jp/rb/14424645/)

**[2]neuralnetworksanddeeplearning** [Webpage](http://neuralnetworksanddeeplearning.com/chap1.html)

**[3]Neural Networks and Deep Learning** [Coursera](https://www.coursera.org/learn/neural-networks-deep-learning)

**[4]Wikipedia ディープラーニング** [Webpage](https://ja.wikipedia.org/wiki/%E3%83%87%E3%82%A3%E3%83%BC%E3%83%97%E3%83%A9%E3%83%BC%E3%83%8B%E3%83%B3%E3%82%B0)
