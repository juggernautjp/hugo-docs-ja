---
aliases:
- /overview/usage/
- /extras/livereload/
- /doc/usage/
- /usage/
categories:
- getting started
date: "2017-02-01"
description: Hugo の CLI は十分な機能を備えていますが、コマンドラインでの操作経験がほとんどない人でも簡単に使用できます。
draft: false
keywords:
- usage
- livereload
- command line
- flags
linktitle: 基本的な使用方法
menu:
  docs:
    parent: getting-started
    weight: 40
publishdate: "2017-02-01"
sections_weight: 40
title: 基本的な使用方法
toc: true
weight: 40
---

以下は、Hugo プロジェクトの開発中に使用する最も一般的なコマンドの説明です。Hugo の CLI を包括的に見るには、[「コマンドライン リファレンス」][commands] を参照してください。

## インストールをテストする {#test-installation}

[Hugo をインストール][install] したら、それがあなたの `PATH` にあることを確認してください。Hugo が正しくインストールされたかどうかは、以下のように `help` コマンドで確認することができます。

```txt
hugo help
```

コンソールに表示される出力は、以下のようなものになるはずです。

```txt
hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at https://gohugo.io/.

Usage:
  hugo [flags]
  hugo [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  config      Print the site configuration
  convert     Convert your content to different formats
  deploy      Deploy your site to a Cloud provider.
  env         Print Hugo version and environment info
  gen         A collection of several useful generators.
  help        Help about any command
  import      Import your site from others.
  list        Listing out various types of content
  mod         Various Hugo Modules helpers.
  new         Create new content for your site
  server      A high performance webserver
  version     Print the version number of Hugo

Flags:
  -b, --baseURL string             hostname (and path) to the root, e.g. https://spf13.com/
  -D, --buildDrafts                include content marked as draft
  -E, --buildExpired               include expired content
  -F, --buildFuture                include content with publishdate in the future
      --cacheDir string            filesystem path to cache directory. Defaults: $TMPDIR/hugo_cache/
      --cleanDestinationDir        remove files from destination not found in static directories
      --config string              config file (default is path/config.yaml|json|toml)
      --configDir string           config dir (default "config")
  -c, --contentDir string          filesystem path to content directory
      --debug                      debug output
  -d, --destination string         filesystem path to write files to
      --disableKinds strings       disable different kind of pages (home, RSS etc.)
      --enableGitInfo              add Git revision, date, author, and CODEOWNERS info to the pages
  -e, --environment string         build environment
      --forceSyncStatic            copy all files when static is changed.
      --gc                         enable to run some cleanup tasks (remove unused cache files) after the build
  -h, --help                       help for hugo
      --ignoreCache                ignores the cache directory
      --ignoreVendorPaths string   ignores any _vendor for module paths matching the given Glob pattern
  -l, --layoutDir string           filesystem path to layout directory
      --log                        enable Logging
      --logFile string             log File path (if set, logging enabled automatically)
      --minify                     minify any supported output format (HTML, XML etc.)
      --noChmod                    don't sync permission mode of files
      --noTimes                    don't sync modification time of files
      --panicOnWarning             panic on first WARNING log
      --poll string                set this to a poll interval, e.g --poll 700ms, to use a poll based approach to watch for file system changes
      --printI18nWarnings          print missing translations
      --printMemoryUsage           print memory usage to screen at intervals
      --printPathWarnings          print warnings on duplicate target paths etc.
      --printUnusedTemplates       print warnings on unused templates.
      --quiet                      build in quiet mode
      --renderToMemory             render to memory (only useful for benchmark testing)
  -s, --source string              filesystem path to read files relative from
      --templateMetrics            display metrics about template executions
      --templateMetricsHints       calculate some improvement hints when combined with --templateMetrics
  -t, --theme strings              themes to use (located in /themes/THEMENAME/)
      --themesDir string           filesystem path to themes directory
      --trace file                 write trace to file (not useful in general)
  -v, --verbose                    verbose output
      --verboseLog                 verbose logging
  -w, --watch                      watch filesystem for changes and recreate as needed

Use "hugo [command] --help" for more information about a command.
```

## `hugo` コマンド {#the-hugo-command}

最も一般的な使用方法は、カレントディレクトリを入力ディレクトリとして `hugo` を実行することです。

これにより、デフォルトで `public/` ディレクトリに Web サイトを生成しますが、[サイト設定][config] の `publishDir` フィールドを変更することで出力ディレクトリをカスタマイズできます。

`hugo` コマンドは、サイトを `public/` ディレクトリにレンダリングし、Web サーバーにデプロイする準備ができました。

```txt
hugo
0 draft content
0 future content
99 pages created
0 paginator pages created
16 tags created
0 groups created
in 90 ms
```

## 下書き、公開予定、期限切れのコンテンツ {#draft-future-and-expired-content}

Hugo では、コンテンツの [フロントマター][front matter] に `draft` や `publishdate`、さらには `expirydate` を設定できます。デフォルトでは、Hugo は以下のコンテンツを公開しません。

1. 将来の `publishdate` 値を持つコンテンツ (公開予定)
2. `draft: true` ステータスを持つコンテンツ (下書き)
3. 過去の `expirydate` 値を持つコンテンツ (期限切れ)

これらの 3 つは、ローカルでの開発とデプロイの両方で、それぞれ `hugo` と `hugo server` に以下のフラグを追加するか、あるいは [設定][config] で同じ名前のフィールド (`--` を含まない) に割り当てられたブール値の変更によってオーバーライドすることができます。

1. `--buildFuture`
2. `--buildDrafts`
3. `--buildExpired`

## LiveReload

Hugo には [LiveReload](https://github.com/livereload/livereload-js) が組み込まれています。追加でインストールが必要なパッケージはありません。 サイト開発中に Hugo を使う一般的な方法は、`hugo server` コマンドで Hugo のサーバーを実行し、変更を監視することです。

```bash
hugo server
0 draft content
0 future content
99 pages created
0 paginator pages created
16 tags created
0 groups created
in 120 ms
Watching for changes in /Users/yourname/sites/yourhugosite/{data,content,layouts,static}
Serving pages from /Users/yourname/sites/yourhugosite/public
Web Server is available at http://localhost:1313/
Press Ctrl+C to stop
```

これは、完全に機能する Web サーバーを実行すると同時に、[プロジェクト組織][dirs] の以下の領域で追加、削除、または変更がないか、ファイルシステムを監視するものです。

* `/static/*`
* `/content/*`
* `/data/*`
* `/i18n/*`
* `/layouts/*`
* `/themes/<CURRENT-THEME>/*`
* `config`

変更を加えるたびに、Hugo は同時にサイトを再構築し、コンテンツの提供を継続します。ビルドが終了するとすぐに、LiveReload はブラウザに静かにページをリロードするように指示します。

ほとんどの Hugo のビルドは非常に高速なので、ブラウザで直接サイトを見ない限り、変更に気づかないかもしれません。つまり、2番目のモニター (または現在のモニターの別の半分) にサイトを開いておけば、テキストエディターから離れることなく、最新版の Web サイトを表示することができます。

{{% note "Closing `</body>` Tag"%}}
Hugo は LiveReload の `<script>` をテンプレートの終了 `</body>` の前に挿入するため、このタグが存在しない場合は動作しないことに注意してください。
{{% /note %}}

### 保存したページに自動的にリダイレクトする {#redirect-automatically-to-the-page-you-just-saved}

複数のドキュメントで作業していて、できるだけリアルタイムにマークアップを表示したい場合、ドキュメント間をジャンプし続けるのは理想的ではありません。
幸いなことに、Hugo には、これに対する簡単で組み込み型のシンプルなソリューションがあります。それは `--navigateToChanged` というフラグです。

### LiveReload を無効にする {#disable-livereload}

LiveReload は、Hugo が生成するページに JavaScript を挿入することによって機能します。 このスクリプトは、ブラウザの Web ソケット クライアントから Hugo Web ソケット サーバーへの接続を作成します。

以下の方法で、LiveReload を簡単に無効にすることができます。

```txt
hugo server --watch=false
```

または

```txt
hugo server --disableLiveReload
```

後者のフラグは、以下を追加することで省略できます。

{{< code-toggle file="config" >}}
disableLiveReload = true
{{< /code-toggle >}}

## Web サイトをデプロイする {#deploy-your-website}

ローカルでの Web 開発のために `hugo server` を実行した後、サイトを再構築するために *コマンドの `server` の部分なしで*、最後に `hugo` を実行する必要があります。その後、 `public/` ディレクトリを本番用の Web サーバにコピーすることで、サイトをデプロイできます。

Hugo は静的な Web サイトを生成するので、任意の Web サーバーを使って、サイトを *どこでも* ホスティングできます。 Hugo コミュニティが提供するホスティングや自動デプロイの方法については、[「ホスティングとデプロイ」][hosting] を参照してください。

{{% warning "Generated Files are **NOT** Removed on Site Build" %}}
`hugo` を実行しても、ビルド前に生成されたファイルは削除されません。 これは、`hugo` コマンドを実行する前に、`public/` ディレクトリ (またはフラグや設定ファイルで指定した publish ディレクトリ) を削除する必要があることを意味します。 これらのファイルを削除しないと、生成されたサイトに間違ったファイル (下書きや将来の投稿など) が残るリスクがあります。
{{% /warning %}}


[commands]: /commands/
[config]: /getting-started/configuration/
[dirs]: /getting-started/directory-structure/
[front matter]: /content-management/front-matter/
[hosting]: /hosting-and-deployment/
[install]: /getting-started/installing/
