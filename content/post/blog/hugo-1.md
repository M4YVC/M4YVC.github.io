---
title: "Hugoで生成した静的サイトをGitHub Pagesにデプロイする 1"
description: 
slug: "hugo-1"
date: 2022-05-20T11:36:32+09:00
lastmod: 2022-05-20T11:36:32+09:00
aliases:
tags:
  - Hugo
  - Git
categories:
  - ブログ
image:
draft: true
---

当ブログは、[Hugo](https://gohugo.io/)で静的サイトを生成し、[GitHub Pages](https://docs.github.com/ja/pages/getting-started-with-github-pages/about-github-pages)にデプロイしています。

ブログのテーマは[Stack](https://github.com/CaiJimmy/hugo-theme-stack)をお借りしています。

HugoのインストールからGitHub Pagesに自動でデプロイするところまでの手順をメモします。



## 開発環境

- OS: Windows10 Pro
- Chocolatey v0.11.2 (Hugoのインストールに使用)
- VS Code v1.67.1
- Hugo Extended v0.99.0
- [Stack](https://github.com/CaiJimmy/hugo-theme-stack) v3.11.0



## Hugoをインストールする

私はChocolateyでインストールしました。<br/>
インストール方法は[公式サイト](https://gohugo.io/getting-started/installing/)に書いてあります。

Extended版をインストールします。
```
$ choco install hugo-extended -confirm
```

バージョンを確認！
```
$ hugo version
hugo v0.99.0-1de333e7a3fc863672ec6d6cd53ba66dbcdd2305+extended　windows/amd64 BuildDate=2022-05-16T08:10:56Z VendorInfo=gohugoio
```


## Hugoでサイトを生成する

### 準備

`<ブログ名>`というフォルダが作成されます。
```
$ hugo new site <ブログ名>
Congratulations! Your new Hugo site is created in X:\workspace\ブログ名.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```


### テーマ追加

[Stack](https://github.com/CaiJimmy/hugo-theme-stack)というテーマをお借りしました。
テーマは[ここ](https://themes.gohugo.io/)に色々あります。<br/>

`themes/<テーマ名>`フォルダにテーマのリポジトリをサブモジュールを追加します。
なお、テーマは修正したくなると思ったのでフォークしました。
```
$ cd <ブログ名>
$ git init
$ git submodule add <追加するテーマのリポジトリURL> themes/<テーマ名>
```

### テーマのサンプルを拝借

とりあえずテーマに用意されているサンプルをコピーします。
```
$ xcopy .\themes\hugo-theme-stack\exampleSite\content content /e
```

サンプルの`config.yaml`ファイルを拝借し、`config.toml`ファイルは削除します。
```
$ copy .\themes\hugo-theme-stack\exampleSite\config.yaml
$ rm .\config.toml
```

### ~~ひゅ～～～～ Go!!!~~
ローカルホストで実行できます。

`-D`は下書きのページ(draft: true)も表示してくれるみたいです。
```
$ hugo server
または
$ hugo server -D
```

[localhost:1313](http://localhost:1313)をブラウザで開き、このようなサイトが表示されれば成功です。
![](example-site.bmp)


作成中・・・・

