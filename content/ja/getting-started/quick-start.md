---
aliases:
- /quickstart/
- /overview/quickstart/
authors:
- Shekhar Gulati
- Ryan Watters
categories:
- getting started
date: "2013-07-01"
description: 美しい「Ananke」テーマを使って Hugo サイトを作成します。
draft: false
keywords:
- quick start
- usage
linktitle: クイックスタート
menu:
  docs:
    parent: getting-started
    weight: 10
publishdate: "2013-07-01"
sections_weight: 10
title: クイックスタート
toc: true
weight: 10
---

{{% note %}}
このクイックスタートでは、例として `macOS` を使用します。他のオペレーティングシステムに Hugo をインストールする方法については、[インストール](/getting-started/installing) を参照してください。

このチュートリアルを実行するには、[Git のインストール](https://git-scm.com/downloads) が必要です。

Hugo を学習するその他の方法 (本やビデオ チュートリアルなど) については、[外部学習リソース](/getting-started/external-learning-resources/) ページを参照してください。
{{% /note %}}

## ステップ 1: Hugo をインストールする {#Step-1-install-hugo}

**Hugo の拡張版** をインストールします (現在使用しているテーマに必要です)。

{{% note %}}
MacOS 用のパッケージマネージャである `Homebrew` と `MacPorts` は、それぞれ [brew.sh](https://brew.sh/) と [macports.org](https://www.macports.org/) からインストールすることができます。Windows などを使っている場合は、[インストール](/getting-started/installing) を参照してください。
{{% /note %}}

```bash
brew install hugo
# または
port install hugo
```

新しいインストールを確認するには、以下を実行します。

```bash
hugo version
# 出力例: hugo v0.104.2+extended darwin/amd64 BuildDate=unknown
```

`extended` であることが明記されているはずです。そうでない場合は、アンインストールし、別のインストール方法を試してください。

{{< asciicast ItACREbFgvJ0HjnSNeTknxWy9 >}}

## ステップ 2: 新しいサイトを作成する {#step-2-create-a-new-site}

```bash
hugo new site quickstart
```

上記のコマンド実行により、`quickstart` という名前のフォルダに新しい Hugo サイトが作成されます。

{{< asciicast 3mf1JGaN0AX0Z7j5kLGl3hSh8 >}}

## ステップ 3: テーマを追加する {#step-3-add-a-theme}

選択可能なテーマの一覧は、[themes.gohugo.io](https://themes.gohugo.io/) を参照してください。このクイックスタートでは、美しい [Ananke テーマ](https://themes.gohugo.io/gohugo-theme-ananke/) を使用します。

まず、GitHub からテーマをダウンロードして、サイトの `themes` ディレクトリに追加します。

```bash
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

次に、テーマをサイト構成に追加します。

```bash
echo theme = \"ananke\" >> config.toml
```

{{< asciicast 7naKerRYUGVPj8kiDmdh5k5h9 >}}

## ステップ 4: コンテンツを追加する {#step-4-add-some-content}

手動でコンテンツファイルを作成し (たとえば `content/<CATEGORY>/<FILE>.<FORMAT>` として)、その中にメタデータを提供することができますが、`new` コマンドを使っていくつかのことを代わりに行うことができます (タイトルや日付を追加するような)。

```txt
hugo new posts/my-first-post.md
```

{{< asciicast eUojYCfRTZvkEiqc52fUsJRBR >}}

必要に応じて、新しく作成されたコンテンツ ファイルを編集します。次のような内容で始まります。

```md
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---

```

{{% note %}}
ドラフトはデプロイされません。投稿を終えたら、投稿のヘッダを更新して `draft: false` と記述してください。詳細は [こちら](/getting-started/usage/#draft-future and-expired-content) を参照してください。
{{% /note %}}

## ステップ 5: Hugo サーバーを起動する {#step-5-start-the-hugo-server}

次に、[drafts](/getting-started/usage/#draft-future-and-expired-content) を有効にして Hugo サーバーを起動します。

{{< asciicast BvJBsF6egk9c163bMsObhuNXj >}}

```txt
▶ hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

**新しいサイト [http://localhost:1313/](http://localhost:1313/) に移動してください。**

新しいコンテンツを自由に編集または追加してください。Hugo サーバーが実行されている間、すぐにブラウザーに変更が表示されます。 (Web ブラウザーを強制的に更新する必要がある場合があります。通常は Ctrl-R などが機能します。)

## ステップ 6: テーマをカスタマイズする {#step-6-customize-the-theme}

新しいサイトはすでに素晴らしい出来栄えですが、一般公開する前に少し手を加えたいところです。

### サイト構成 {#site-configuration}

テキストエディタで `config.toml` を開いてください。

```toml
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```

上記の `title` を個人的なものに置き換えてください。また、すでにドメインが準備されている場合は、`baseURL` を設定します。なお、この値はローカルの開発サーバーを動かす場合には必要ありません。

{{% note %}}
**ヒント:** Hugo サーバーの実行中にサイト構成またはサイト内のその他のファイルに変更を加えると、ブラウザに変更がすぐに反映されますが、[キャッシュのクリア](https://kb.iu.edu/d/ahic) が必要な場合があります。
{{% /note %}}

テーマ固有の設定オプションについては、[テーマサイト](https://github.com/theNewDynamic/gohugo-theme-ananke) を参照してください。

**テーマのカスタマイズについては、[テーマのカスタマイズ](/themes/customizing/) を参照してください。**

### ステップ 7: 静的ページを作成する {#step-7-build-static-pages}

方法は簡単で、以下のコマンドを実行するだけです。

```txt
hugo -D
```

デフォルトでは `./public/` ディレクトリに出力されます (`-d`/`--destination` フラグで変更するか、設定ファイルで `publishdir` を設定してください)。

