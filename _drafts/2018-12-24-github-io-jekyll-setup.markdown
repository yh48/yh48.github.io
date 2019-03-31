---
layout: post
title:  "JekyllでGithubPagesを作成手順"
date:   2018-12-24 21:06:26 +0900
categories: jekyll update
---

:toc

# はじめに

より自由に、記事を書くため、github.ioを使うつもりです。

よろしくお願い致します。

この機会に、github pagesの作成方法と手順をまとめます。

## github pages とは？

[GithubPages](https://pages.github.com/)、GitHubが提供している静的サイトのホスティングサービス。
Githubリポジトリから、ウェブサイトを作成出来ます。

# 手順

## jekyll をインストールとサイト作成

基本的に、全部の手順は[ここ](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)に載せています。

1. Ruby環境確認

略、しかし、rbenvから、最新バーションをインストールはおすすめです。

2. [github-pages](https://github.com/github/pages-gem)をインストール

```bash
gem github-pages
```

3. サイトを作成、確認

```bash
jekyll new site_name
cd site_name
jekyll serve
```

ブラウザから確認できます。

4. githubにPush

略、基本的に、Githubの新規Repoの提示を従います。
