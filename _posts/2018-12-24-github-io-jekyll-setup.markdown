---
layout: post
title:  "JekyllでGithubPagesを作成手順"
date:   2018-12-24 21:06:26 +0900
categories: jekyll update
---

# はじめに

より自由に、記事を書くため、github.ioを使うつもりです。

よろしくお願い致します。

# インストール

基本的に、全部の手順は[ここ](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)に載せています。

## Ruby環境確認

略、しかし、rbenvから、最新バーションをインストールはおすすめです。

## [github-pages](https://github.com/github/pages-gem)をインストール

```bash
gem github-pages
```

## サイトを作成、確認

```bash
jekyll new site_name
cd site_name
jekyll serve
```

ブラウザから確認できます。

## githubにPush

略、基本的に、Githubの新規Repoの提示を従います。

# 設定

簡単な設定は、ファイル

```
_config.yml
```

から変更出来ます。

## テーマを変更

テーマは[Supported themes](https://pages.github.com/themes/)　から確認できます。
基本的に
