---
layout: post
title:  "Deep Learning Basics"
date:   2019-01-01 21:00:00 +0900
categories: deeplearning
---

* content
{:toc}

# 要約

自分の理解ために、深層学習の基礎概念をまとめます。

深層学習の概念が多いすぎで、覚えしにくい、自分の認識からまとめます。


# 深層学習の目的と原理

**深層学習**　は、多層のニューラルネットワークを用いて機械学習です。

基本的に、学習のプロセスは以下です：


**機械学習**

X, y

パラメタを調整

- 学習段階
- 予測段階

###　ニューラルネットワークの予測と学習

#### 予測のプロセス



#### 学習のプロセス



最適なパラメータを見つけるのプロセスです。

学習段階のポイントは以下です：

- 学習の目標：**損失関数** 最小化
- 学習手法：**誤差の逆伝播（Backpropagation）**
- 手法理論：**合成関数の微分の法則（チェインルール）** と　**勾配降下法**

**Neurons**

**損失関数（LossFunction）**

他クラス分類を行う時に、**交差エントロピー誤差**　を用いる場合が多くあります。

$$

$$

下記は斎藤さんにより：

- Step-1 ミニバッチ
  - 訓練データの中からランダムに複数のデータを選ぶ出す
- Step-2 勾配の算出
  - 誤差逆伝播法により、各重みパラメータに関する損失関数の勾配を求める
- Step-3　パラメータの更新
  - 勾配を使って重みパラメータを更新する
- Step-4　繰り返す
  - Step-1, Step-2, Step-3 を必要な回数だけ繰り返す

## 実装の時の概念


**バッチ学習**：

**ミニバッチ学習**：


**勾配降下法Gradient Descent**:

**確率的勾配降下法Stochastic Gradient Descent**:




**多層ニューラルネットワークの構造**：

- 入力層
- 隠れ層
- 出力層

(Sometimes it is called multilayer perceptrons or MLPs, due to historical　reason, though the neurons are sigmoid neurons)

## サンプル

### Iris

### Handwritten digits



# 学習の過程


# 名詞


**パーセプトロン Perceptron**:
takes several binary inputs, x1,x2,…, and produces a single binary output:

[wikipedia](https://ja.wikipedia.org/wiki/%E3%83%91%E3%83%BC%E3%82%BB%E3%83%97%E3%83%88%E3%83%AD%E3%83%B3)

**シグモイド関数 sigmoid function**



[wikipedia](https://ja.wikipedia.org/wiki/%E3%82%B7%E3%82%B0%E3%83%A2%E3%82%A4%E3%83%89%E9%96%A2%E6%95%B0)


# References

**Neural Networks and Deep Learning** [Coursera](https://www.coursera.org/learn/neural-networks-deep-learning)

**neuralnetworksanddeeplearning** [Webpage](http://neuralnetworksanddeeplearning.com/chap1.html)
