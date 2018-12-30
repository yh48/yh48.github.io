---
layout: post
title:  "December Paper Readings"
date:   2018-12-31 21:00:00 +0900
categories: reading
---

* content
{:toc}

# [KDD2018] I Know You’ll Be Back: Interpretable New User Clustering and Churn Prediction on a Mobile Social App

**Source**: [I Know You’ll Be Back: Interpretable New User Clustering and Churn Prediction on a Mobile Social App](https://www.kdd.org/kdd2018/accepted-papers/view/i-know-youll-be-back-interpretable-new-user-clustering-and-churn-prediction)

Analysis SnapChat data, including data, and ego-network data, proposed method of clustering and interpreting user groups use KMeans, and predict chances of user churn use LSTM.

Actually it can divide into two parts:

- User clustering part
- Churn prediction part

## User Clustering part

- Zero-shot discovery of typical user types
- Handling correlated multi-dimensional behavior data
- Address noises and outliers
- Interpretable clustering result


No complicated algorithms came out, but it is very interesting that the auther did the following process to make result robust and interpretable:

- Clustering on each of single feature
- Combine them together
- Multi-feature clustering


## Churn prediction part

Churn prediction problem are addressing in the second part. The main challenges are:

- Modeling sequential behavior data
- Handling skewed, sparse, correlated activities
- Leveraging underlying user types

### Solutions

([TODO]: The following part, haven't figure out completely, need to read later)

#### Sequence-to-Sequence learning with LSTM

Intrinsic Problem: Convert sequences of arbitrary lengths with temporal dependences into a fixed length vector for further usage.

#### LSTM with activity embedding

Dealing with sparse skewed and correlated activity data, -> add an activity embedding layer in front of the standard LSTM layer.

Connect a fully connected feedforward neural network to the original daily activity vector, which converts users' sparse activity features of each day into distributional activity embeddings.

#### Parallel LSTMs with joint training

Author is trying to leveraging the existing user's knowledge and apply to new user, to improve the new user's churn predicting precious.

- He calculate the user's churn label, and user type of existing users.
- And then calculate the initial behaviors with training set to guess new user's user types.
- And leverage the correlation between user types and churn for better churn prediction


## Some References to read

Twitter-Based User Modeling for News Recommendations

Personalized news recommendation based on click behavior


# Silhouettes: A graphical aid to the interpretation and validation of cluster analysis

Source: [Silhouettes: A graphical aid to the interpretation and validation of cluster analysis](https://www.sciencedirect.com/science/article/pii/0377042787901257)


This is an old paper, I read this just because it was mentioned by the paper above, and want to know the methodlity.

This paper introduced **silhouettes**, actually a score to measure the quality of cluster or instances's connection to a cluster.

You can use silhouette score to:

- Check the cluster's quality
  - high silhouette score: clusters quality is good. Tightly combined within cluster, loosely combined between different clusters
- Check if instances should be assigned to the cluster
  - higher score: more likely, lower score: less likely (probably no where to cluster just an assignment)
- Find the proper K for the K-Means clustering
  - Search K and compare the silhouettes score
  - Choose the K with largest silhouette score
  - Find interpretable cluster

Given cluster result C, For each instance i, the silhouettes score is calculated like:

$$
s(i)=1 - \frac{a(i)}{b(i)}
0
\frac{b(i)}{a(i)} - 1
$$

a(i) is the average distance of i to the other instances within same cluster A ($a(i)=0$ if there is only one instance in the cluster).

D(i, X) is the average distance of i to the instances in cluster X (X not equals to A).

$$b(i)=minimum(D(i, X)), for\ X\in\ C,\ X\neq A$$

# Inferrering causal impact using bayesian structural time-series models

This paper is published by Google. Introduced a method of causal inferance method, and a toolbox (but in R).

It is a good improvement of some old methods like DID.
