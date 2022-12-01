---
aliases: []
authors:
- Michel Racic
categories:
- hosting and deployment
date: "2017-03-12"
description: Firebase の無料利用枠を使用して、静的 Web サイトをホストできます。 これにより、Firebase の NOSQL API にもアクセスできます。
draft: false
keywords:
- hosting
- firebase
linktitle: Firebase でのホスト
menu:
  docs:
    parent: hosting-and-deployment
    weight: 20
publishdate: "2017-03-12"
sections_weight: 20
title: Firebase でのホスト
toc: true
weight: 20
---

## 前提条件 {#assumptions}

1. [Firebase][signup] のアカウントを持っていること。 (持っていない場合は、Google アカウントを使用して無料でサインアップできます)。
2. [クイックスタート][Quick Start] を完了していること、または Hugo の Web サイトをデプロイし、世界と共有する準備ができでいること。

## 初期設定 {#initial-setup}

[Firebase コンソール][console] にアクセスし、新規プロジェクトを作成します (すでにプロジェクトがある場合は除く)。 以下のコマンドにより、`firebase-tools` (node.js) をグローバルにインストールする必要があります。

```bash
npm install -g firebase-tools
```

Firebase (ローカルマシンに設定します) に `firebase login` でログインすると、ブラウザが起動してアカウントが選択できるようになります。 すでにログインしているが間違ったアカウントにログインしている場合は、`Firebase logout` を使用します。

```bash
firebase login
```

Hugo プロジェクトのルートで、以下のように `firebase init` コマンドを使用して、Firebase プロジェクトを初期化します。

```bash
firebase init
```

ここから、以下の手順を実行します。

1. 機能の質問でホスティングを選択します
2. 先ほど設定したプロジェクトを選択します
3. データベース ルール ファイルのデフォルトを受け入れます
4. 公開ディレクトリのデフォルトである `public` を受け入れます
5. シングルページ アプリをデプロイする場合は、質問で [いいえ] を選択します

## デプロイ {#deploy}

Hugo サイトをデプロイするには、以下のように、`firebase deploy` コマンドを実行すれば、すぐにサイトが立ち上がります。

```bash
hugo && firebase deploy
```

## CI 設定 {#ci-setup}

以下のコマンドを使用して、デプロイトークンを生成できます。

```bash
firebase login:ci
```

また、(Wercker などを使って) CI を設定し、トークンを `$FIREBASE_DEPLOY_TOKEN` のようなプライベート変数に追加できます。

{{% note %}}
これはプライベートな秘密であり、パブリック リポジトリには表示されません。 選択した CI を理解し、他の人には見えないことを確認してください。
{{% /note %}}

その後、ビルドにステップを追加して、トークンを使用してデプロイを実行できます。

```bash
firebase deploy --token $FIREBASE_DEPLOY_TOKEN
```

## 参考リンク {#reference-links}

* [Firebase CLI リファレンス](https://firebase.google.com/docs/cli/#administrative_commands)

[console]: https://console.firebase.google.com
[Quick Start]: /getting-started/quick-start/
[signup]: https://console.firebase.google.com/
