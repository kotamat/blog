+++
date = "2015-04-12T22:05:13+09:00"
draft = true
title = "start hugo"

+++

# Hugoを使ってブログを作ってみた

## なんでHugo?

最近wordpressにてサイト作成してみているんですが、 ブログの情報ってDBに入っちゃいますよね。

やっぱりブログとはいえステージング環境とかいれてテーマの修正とかしたいことあるんですけど、 まぁマイグレーションがめんどくさい！

しかもwordpressだとサイトのドメインとかステージング向きじゃない奴とかあると、DB変更しなきゃいけなかったり…

ってことでマイグレーションできる静的なブログツールを探してました。

## じゃあJekyllでいいよね？

Goしたかったんです。GoGo!

## インストール手順

だいたいreadmeみれば書いてありますが。。 https://github.com/spf13/hugo
コントリビュートしないのであればbrewに乗っかっているので、 brewからインストールしてみます。

- brewでインストール
```code
brew install hugo
```
- 新規サイト作成
```code
hugo new sitename
cd sitename
```
- ファイルを作成( XXX.mdを作成すると、/XXX.htmlにサイトが作成されるイメージ)
```code
hugo new about.md
```
- about.mdを編集
- テーマのインストール
```code
git clone --recursive https://github.com/spf13/hugoThemes themes
```
- public/XXX.htmlが作成される
```code
hugo
```
- 一旦サイトに公開
	- `--theme` インストールしたテーマを選んで
	- `--buildDrafts` 表示させる
	- `--watch` mdファイルが変更されたら即時反映
```code
hugo server --theme=hyde --buildDrafts --watch
```

## じゃあgithub pagesに反映してみますか

- サブモジュールの作成
```code
rm -rf public
git submodule add https://github.com/username/username.github.io.git public
```
- アクセス!!
http://username.github.io

## 今までの投稿ファイルもgithubにpush
```code
cd ../
git add .
git commit
git push origin master
```
