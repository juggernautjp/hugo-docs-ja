---
aliases:
- /tutorials/installing-on-windows/
- /tutorials/installing-on-mac/
- /overview/installing/
- /getting-started/install
- /install/
authors:
- Michael Henderson
categories:
- getting started
- fundamentals
date: "2016-11-01"
description: Hugo を macOS、Windows、Linux、OpenBSD、FreeBSD、および Go コンパイラ ツールチェーンが実行可能な任意のマシンにインストールします。
draft: false
keywords:
- install
- pc
- windows
- linux
- macos
- binary
- tarball
linktitle: Hugo をインストールする
menu:
  docs:
    parent: getting-started
    weight: 30
publishdate: "2016-11-01"
sections_weight: 30
title: Hugo をインストールする
toc: true
weight: 30
---

{{% note %}}
「Hugo は Go で書かれている」という話はよく聞きますが、Hugo を楽しむのに Go をインストールする必要はありません。プリコンパイルされたバイナリを入手するだけです。
{{% /note %}}

Hugo は [Go](https://go.dev/) で書かれており、複数のプラットフォームをサポートしています。最新のリリースは [Hugo Releases][releases] で見ることができます。

現在、Hugo では以下のようなビルド済みバイナリを提供しています。

* x64、i386、ARM アーキテクチャ用 macOS (Darwin)
* Windows
* Linux
* OpenBSD
* FreeBSD

Hugo は、Go ツールチェインが動作するところならどこでも、例えば DragonFly BSD, OpenBSD, Plan&nbsp;9, Solaris などの他のオペレーティング システム上でもソースからコンパイルすることができます。サポートされているターゲット OS とコンパイル アーキテクチャの組み合わせの完全なセットについては、<https://go.dev/doc/install/source> を参照してください。

## クイックインストール {#quick-install}

### バイナリ (クロスプラットフォーム) {#binary-cross-platform}

[Hugo Releases][releases] から、お使いのプラットフォームに適したバージョンをダウンロードしてください。一度ダウンロードすれば、バイナリはどこからでも実行できます。グローバルな場所にインストールする必要はありません。これは、共有ホストや特権アカウントを持たない他のシステムでうまく機能します。

使いやすいように、`PATH` のどこかにインストールするのが理想的です。`/usr/local/bin` が最も可能性の高い場所です。

### Docker

現在、Docker 用の公式 Hugo イメージは提供していませんが、右記の最新版ディストリビューションを推奨します: https://hub.docker.com/r/klakegg/hugo/

### Homebrew (macOS)

macOS で [Homebrew][brew] を使っている場合、以下のワンライナーで Hugo をインストールできます。

{{< code file="install-with-homebrew.sh" >}}
brew install hugo
{{< /code >}}

より詳細な説明は、macOS と Windows へのインストールに関する以下のインストールガイドを参照してください。

### MacPorts (macOS)

macOS で [MacPorts][macports] を使用している場合は、以下のワンライナーで Hugo をインストールできます。

{{< code file="install-with-macports.sh" >}}
port install hugo
{{< /code >}}

### Homebrew (Linux)

Linux で [Homebrew][linuxbrew] を使用している場合は、次のワンライナーで Hugo をインストールできます。

{{< code file="install-with-linuxbrew.sh" >}}
brew install hugo
{{< /code >}}

Linux 用の Homebrew のインストール ガイドは、[website][linuxbrew] で入手できます。

### Chocolatey (Windows)

Windows マシンで、パッケージ管理に [Chocolatey][] を使用している場合、以下のワンライナーで Hugo をインストールできます。

{{< code file="install-with-chocolatey.ps1" >}}
choco install hugo -confirm
{{< /code >}}

あるいは、Sass/SCSS の「拡張版」が必要な場合は、以下のコマンドを実行します。

{{< code file="install-extended-with-chocolatey.ps1" >}}
choco install hugo-extended -confirm
{{< /code >}}

### Scoop (Windows)

Windows マシンを使用していて、パッケージ管理に [Scoop][] を使用している場合は、以下のワンライナーで Hugo をインストールできます。

```bash
scoop install hugo
```

または、拡張版を次のようにインストールします。

```bash
scoop install hugo-extended
```

### ソース {#source}

#### 前提条件となるツール {#prerequisite-tools}

* [Git][installgit]
* [GCC][] (For Windows users only)
* [Go (少なくとも Go 1.11)](https://go.dev/dl/)

#### GitHub からフェッチする {#fetch-from-github}

Hugo 0.48 以降、Hugo は Go 1.11 に組み込まれた Go モジュールのサポートを使用してビルドします。最も簡単な方法は、以下の例のように GOPATH の外のディレクトリに Hugo をクローンすることです。

{{< code file="from-gh.sh" >}}
mkdir $HOME/src
cd $HOME/src
git clone https://github.com/gohugoio/hugo.git
cd hugo
go install --tags extended
{{< /code >}}

Sass/SCSS サポートが不要な場合は、`--tags extended` を削除してください。

{{% note %}}

##### Windowsにインストールする場合 {#for-installation-on-windows}

* 上記の環境変数 `$HOME` を `%USERPROFILE%` に置き換えてください。
* `--tags extended` バージョンをインストールすると、`"gcc": executable file not found in %PATH%` というエラーが発生する場合があります
  * `gcc` コマンドがインストールされていることを確認し、それを `%PATH%` に追加してください。
  * テスト済みで、正常にビルドされているため、"MinGW "を推奨します。

{{% /note %}}

## macOS

### 前提条件 {#assumptions}

1. macOS ターミナルを開く方法を知っています。
2. 最新の 64 ビット Mac を使用しています。
3. サイトの開始点として `~/Sites` を使用します。 (`~/Sites` は例として使用されています。コマンドラインとファイル システムに十分に精通している場合は、手順に従って問題なく実行できるはずです。)

### 方法を選択する {#pick-your-method}

Mac　に Hugo をインストールするには、以下の 3 つの方法があります。

1. [Homebrew][brew] (`brew`) や [MacPorts][macports] (`port`) などのパッケージ マネージャー
2. 配布物 (つまり、tarball)
3. ソースからのビルド

Mac に Hugo をインストールする「最良の」方法というのはありません。あなたの用途に最も適した方法を使うべきです。

#### 長所と短所 {#pros-and-cons}

前述した方法にはそれぞれ長所と短所があります。

1. **パッケージ マネージャー** パッケージマネージャを使用するのは最も簡単な方法で、メンテナンスの手間も最小限で済みます。欠点は深刻ではありません。デフォルトのパッケージは最新のリリース用なので、次のリリースまでバグフィックスはありません (つまり、Homebrew で `--HEAD` オプションを付けてインストールしない限り)。他のチームと調整する必要があるため、リリースは数日遅れるかもしれません。それでも、安定した、広く使われているソースから作業をしたいのであれば、このインストール方法をお勧めします。パッケージマネージャはうまく機能しますし、更新も簡単です。

2. **Tarball** tarball からのダウンロードとインストールも簡単ですが、Homebrew よりも少しコマンドラインのスキルが必要です。アップデートも簡単で、新しいバイナリでこのプロセスを繰り返すだけです。このため、コンピュータに複数のバージョンを置く柔軟性があります。もし `brew` を使いたくなければ、tarball/バイナリ が良い選択でしょう。

3. **ソースからのビルド** ソースからビルドするのが一番手間がかかります。ソースからビルドすることのメリットは、機能やバグフィックスを追加するためにリリースを待つ必要がないことです。デメリットは、セットアップの管理に時間を割く必要があることで、管理は可能ですが、先の2つの選択肢より多くの時間を必要とします。

{{% note %}}
ソースからのビルドは熟練したコマンドライン ユーザーにとって魅力的なので、このガイドでは Homebrew と Tarball を使った Hugo をインストールすることに重点を置きます。
{{% /note %}}

### Brew で Hugo をインストールする {#install-hugo-with-brew}

{{< youtube WvhCGlLcrF8 >}}

#### ステップ 1: `brew` をまだインストールしていない場合はインストールします {#step-1-install-brew-if-you-havent-already}

`brew` のウェブサイト <https://brew.sh> にアクセスし、そこに書かれている指示に従ってください。最も重要なステップは、コマンドラインからのインストールです。

{{< code file="install-brew.sh" >}}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{{< /code >}}

#### ステップ2: `brew` コマンドを実行して、`hugo` をインストールします。{#step-2-run-the-brew-command-to-install-hugo}

`brew` を使用して Hugo をインストールするのは、以下のように簡単です。

{{< code file="install-brew.sh" >}}
brew install hugo
{{< /code >}}

Homebrew が正常に動作していれば、以下のような画面が表示されるはずです。

```txt
==> Downloading https://homebrew.bintray.com/bottles/hugo-0.21.sierra.bottle.tar.gz
######################################################################### 100.0%
==> Pouring hugo-0.21.sierra.bottle.tar.gz
🍺  /usr/local/Cellar/hugo/0.21: 32 files, 17.4MB
```

{{% note "Installing the Latest Hugo with Brew" %}}
開発中の最新版が必要な場合は、`brew install hugo` を `brew install hugo --HEAD` に置き換えてください。
{{% /note %}}

`brew` が Hugo を含むようにパスを更新してくれているはずです。新しいターミナルウィンドウを開いて、いくつかのコマンドを実行することで確認できます。

```bash
# hugo の実行ファイルの場所を表示します
which hugo
/usr/local/bin/hugo

# インストールされたバージョンを表示します
ls -l $( which hugo )
lrwxr-xr-x  1 mdhender admin  30 Mar 28 22:19 /usr/local/bin/hugo -> ../Cellar/hugo/0.13_1/bin/hugo

# hugo が正しく動作することを確認します
hugo version
Hugo Static Site Generator v0.13 BuildDate: 2015-03-09T21:34:47-05:00
```

### Tarball から Hugo をインストールする {#install-hugo-from-tarball}s

#### ステップ1: 設置場所を決める {#step-1-decide-on-the-location}

tarball からインストールする場合、バイナリを `/usr/local/bin` にインストールするか、ホームディレクトリにインストールするかを決める必要があります。これには、以下の 3つの場所があります。

1. これを `/usr/local/bin` にインストールして、システム上のすべてのユーザがアクセスできるようにします。これは、実行ファイルの場所としてはかなり標準的なので、良い考えだと思います。欠点は、その場所にソフトウェアを置くために、昇格した特権が必要になるかもしれないことです。また、システム上に複数のユーザーがいる場合、その全員が同じバージョンを実行することになります。新しいリリースを試したい場合、これが問題になることがあります。

2. 自分だけが実行できるように `~/bin` にインストールします。これは、簡単にできて、メンテナンスが簡単で、昇格した特権を必要としないので、良い考えです。欠点は、Hugo を実行できるのが自分だけだということです。あなたのサイトに他のユーザがいれば、そのユーザが自分のコピーを維持しなければなりません。そのため、人々が異なるバージョンを実行することになりかねません。もちろん、これによって、さまざまなリリースを試すことが容易になります。

3. それを `Sites` ディレクトリにインストールします。ビルドしているサイトが 1 つだけなら、これは悪い考えではないでしょう。すべてのものを 1カ所にまとめておくことができます。新しいリリースを試したい場合は、サイト全体のコピーを作成し、Hugo の実行可能ファイルを更新できます。

この 3 つの場所は、すべてあなたのために働くでしょう。このガイドでは、簡潔にするために、2番目のオプションに焦点を当てます。

#### ステップ 2: Tarball をダウンロードする {#step-2-download-the-tarball}

1. ブラウザで <https://github.com/gohugoio/hugo/releases> を開きます。

2. 下にスクロールして、"Latest Release" と書かれた緑色のタグを探し、現在のリリースを見つけます。

3. Mac 用の現在の tarball をダウンロードします。名前は `hugo_X.Y_osx-64bit.tgz` のようなものになり、`X.YY` はリリース番号になります。

4. デフォルトでは、tarball は `~/Downloads` ディレクトリに保存されます。もし、別の場所を使いたい場合は、次の手順で変更する必要があります。

#### ステップ 3: ダウンロードを確認する {#step-3-confirm-your-download}

ダウンロード中に tarball が破損していないことを確認します。

```bash
tar tvf ~/Downloads/hugo_X.Y_osx-64bit.tgz
-rwxrwxrwx  0 0      0           0 Feb 22 04:02 hugo_X.Y_osx-64bit/hugo_X.Y_osx-64bit.tgz
-rwxrwxrwx  0 0      0           0 Feb 22 03:24 hugo_X.Y_osx-64bit/README.md
-rwxrwxrwx  0 0      0           0 Jan 30 18:48 hugo_X.Y_osx-64bit/LICENSE.md
```

`.md` ファイルは Hugo のドキュメントです。 もう 1 つのファイルは実行可能ファイルです。

#### ステップ 4: `bin` ディレクトリにインストールする {#step-4-install-into-your-bin-directory}s

```bash
# 必要に応じて、ディレクトリを作成します
mkdir -p ~/bin

# 作業ディレクトリにします
cd ~/bin

# tarball を解凍します
tar -xvzf ~/Downloads/hugo_X.Y_osx-64bit.tgz
Archive:  hugo_X.Y_osx-64bit.tgz
  x ./
  x ./hugo
  x ./LICENSE.md
  x ./README.md

# 動作することを確認します
./hugo version
Hugo Static Site Generator v0.13 BuildDate: 2015-02-22T04:02:30-06:00
```

環境変数 `PATH` に bin ディレクトリを追加する必要があるかもしれません。`which` コマンドがチェックしてくれます。 `hugo` が見つかれば、そのフルパスを表示します。そうでなければ、何も表示されません。

```bash
# hugo がパスに含まれているかどうかを確認します
which hugo
/Users/USERNAME/bin/hugo
```

`hugo` が `PATH` にない場合:

1. デフォルトのシェル (zsh または bash) を決定します。

   ```bash
   echo $SHELL
   ```

2. プロファイルを編集します。

   デフォルトのシェルが zsh の場合。

    ```zsh
    nano ~/.zprofile
    ```

    デフォルトのシェルが bash の場合。

    ```bash
    nano ~/.bash_profile
    ```

3. 既存の `PATH` に `$HOME/bin` を追加する行を挿入します。

    ```txt
    export PATH=$PATH:$HOME/bin
    ```

4. Control-X を押してから Y を押して、ファイルを保存します。

5. ターミナルを閉じて、新しいターミナルを開き、プロファイルの変更を取得します。もう一度 `which hugo` コマンドを実行して、変更を確認します。


Hugo が正常にインストールされました。

### Mac でソースからビルドする {#build-from-source-on-mac}

Hugo を自分でコンパイルしたい場合は、Go (別名 Golang) をインストールする必要があります。 [Go Web サイトから Go を直接インストール](https://go.dev/dl/) するか、または Homebrew 経由で以下のコマンドを使用できます。

```txt
brew install go
```

#### ステップ1: ソースを入手する {#step-1-get-the-source}

特定のバージョンの Hugo をコンパイルしたい場合は、<https://github.com/gohugoio/hugo/releases> にアクセスし、希望のバージョンのソースコードをダウンロードしてください。 
Hugo を最新の変更点 (バグを含むかもしれません) をすべて含んでコンパイルしたい場合、以下のコマンドを実行して Hugo リポジトリをクローンしてください。

```txt
git clone https://github.com/gohugoio/hugo
```

{{% warning "Sometimes \"Latest\" = \"Bugs\""%}}
Hugo リポジトリを直接クローンすることは、良い面と悪い面を一緒に取ることを意味します。Hugo の最新バージョンを使用することで、最新の機能やバグに影響されやすくなります。あなたのフィードバックはありがたいものです。もし最新リリースにバグを見つけたら、[GitHub に issue を作成してください](https://github.com/gohugoio/hugo/issues/new)。
{{% /warning %}}

#### ステップ2: コンパイルする {#step-2-compiling}

ソースのあるディレクトリを作業ディレクトリにし、Hugo の依存関係を取得します。

```txt
mkdir -p src/github.com/gohugoio
ln -sf $(pwd) src/github.com/gohugoio/hugo

go get
```

これにより、依存関係の絶対最新バージョンが取得されます。 Hugo のビルドに失敗した場合、依存関係の作成者が重大な変更を導入した結果である可能性があります。

ディレクトリを適切に構成したら、以下のコマンドで Hugo をコンパイルします。

```txt
go build -o hugo main.go
```

次に、`hugo` 実行可能ファイルを `$PATH` のどこかに配置します。 これで、Hugo を使用する準備が整いました。

## Windows

以下は、Windows PC に Hugo をインストールするための完全なガイドとなることを目的としています。

{{< youtube G7umPCU-8xc >}}

### Windows の前提条件 {#assumptions-for-windows}

1. 新しいプロジェクトの出発点として `C:\Hugo\Sites` を使用します。
2. `C:\Hugo\bin` に実行ファイルを保存します。

### ディレクトリを設定する {#set-up-your-directories}

Hugo 実行可能ファイル、[コンテンツ][content]、および生成された Hugo Web サイトを保存する場所が必要です。

1. Windows エクスプローラーを起動します。
2. C ドライブに Hugo が必要だと仮定して、新しいフォルダーー `C:\Hugo` を作成しますが、これはどこにでも移動できます。
3. Hugo フォルダーにサブフォルダーを作成します: `C:\Hugo\bin`
4. Hugo に別のサブフォルダーーを作成します: `C:\Hugo\Sites`

### テクニカル ユーザー {#technical-users}

1. [Hugo Releases][releases] から最新の zip 圧縮された Hugo 実行ファイルをダウンロードします。
2. すべてのコンテンツを `..\Hugobin` フォルダーに解凍します。
3. Windows のコマンドライン (cmd、"DOS") を開き、`hugo.exe` の実行ファイルを PATH に追加します。
    * `set PATH=%PATH%;C:\Hugo\bin` を実行して、現在開いているコマンド ボックスの PATH に Hugo を含めます。
    * `setx PATH "%PATH%;C:\Hugo\bin"` を実行して、新しく開いたすべてのコマンド ボックスの PATH に Hugo を設定します。
      * 注意: "set" ではなく "setx"、さらに構文は 'key=val' ではなく 'key "val"' です。 

> [Git for Windows パッケージ](https://gitforwindows.org/) の "Git CMD" は、Windows ネイティブコマンドの [set](https://ss64.com/nt/set.html) と [setx](https://ss64.com/nt/setx.html) にも使えますが、"Git Bash" や PowerShell、その他の異なるコマンドを持つ "CLI" には使用できません。

### 技術力の低いユーザー {#less-technical-users}

1. [Hugo Releases][releases] のページに移動します。
2. 一番上に最新のリリースが発表されています。 リリース アナウンスの一番下までスクロールして、ダウンロードを表示します。 それらはすべて ZIP ファイルです。
3. 一番下の Windows のファイル (アルファベット順なので Windows が最後) を探し、32 ビットか 64 ビットかに応じて、32 ビットか 64 ビットのどちらかのファイルをダウンロードしてください。(わからない場合は、[こちらをご覧ください](https://esupport.trendmicro.com/en-us/home/pages/technical-support/1038680.aspx)。)
4. ZIP ファイルを `C:\Hugo\bin` フォルダーーに移動します。
5. ZIP ファイルをダブルクリックして、その内容を解凍します。 内容を必ず同じ `C:\Hugo\bin` フォルダーーに解凍してください。別の場所に解凍するように指示しない限り、Windows はデフォルトでこれを行います。
6. これで、hugo 実行可能ファイル (`hugo.exe`)、`LICENSE`、および `README.md` の 3 つの新しいファイルができたはずです。

ここで、Windows の PATH 設定に Hugo を追加する必要があります。

#### Windows 10 ユーザー向け {#for-windows-10-users}

* **スタート** ボタンを右クリックします。
* **システム** をクリックします。
* 右側の **システムの詳細設定** をクリックします。
* 下部にある **環境変数...** ボタンをクリックします。
* [ユーザー環境変数] セクションで、[パス] というラベルの付いた行を選択し、[編集...] ボタンをクリックします。
* **参照...** ボタンをクリックし、`hugo.exe` を解凍したディレクトリを選択します。上記の手順で行った場合は `C:\Hugo\bin` です。 *パス エントリは、バイナリ自体ではなく、Hugo が存在するフォルダーーである必要があります。*
* すべてのウィンドウで [OK] をクリックして終了します。

#### Windows 10 ユーザー向け {#for-windows-7-and-8x-users}

Windows 7 および 8.1 には、Windows 10 に含まれる簡単なパスエディターが含まれていないため、これらのプラットフォームの技術者でないユーザーは、[Windows 環境変数エディター][Windows Environment Variables Editor] などの無料のサードパーティ製パスエディタをインストールすることをお勧めします。

### 実行可能ファイルを確認する {#verify-the-executable}

いくつかのコマンドを実行して、実行可能ファイルを実行する準備ができていることを確認してから、サンプル サイトをビルドして開始します。

#### 1. コマンドプロンプトを開く {#1-open-a-command-prompt}

プロンプトで `hugo help` と入力し、<kbd>Enter</kbd> キーを押します。以下の行で始まる出力が表示されるはずです。

```txt
hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at https://gohugo.io/.
```

上記の出力が表示されれば、インストールは完了です。そうでない場合は、`hugo.exe` ファイルを置いたパスと、そのパスを `PATH` 変数に追加したときに正しくタイプしたかどうかを再度確認してください。それでも出力が得られない場合は、[Hugo ディスカッション フォーラム][forum] を検索して、他の人がすでに私たちの問題を解決していないかどうかを確認してください。もし見つからない場合は、"Support" カテゴリにメモを書き、コマンドとその出力を必ず書いてください。

プロンプトで、ディレクトリを `Sites` ディレクトリに変更します。

```txt
C:\Program Files> cd C:\Hugo\Sites
C:\Hugo\Sites>
```

#### 2. コマンドを実行する {2-run-the-command}

新しいサイトを生成するためのコマンドを実行します。サイト名は `example.com` を使用します。

```txt
C:\Hugo\Sites> hugo new site example.com
```

これで、`C:\Hugo\Sites\example.com` にディレクトリができたはずです。 そのディレクトリに移動し、内容を一覧表示します。 以下のような出力が得られるはずです。

```txt
C:\Hugo\Sites> cd example.com
C:\Hugo\Sites\example.com> dir
Directory of C:\hugo\sites\example.com

04/13/2015  10:44 PM    <DIR>          .
04/13/2015  10:44 PM    <DIR>          ..
04/13/2015  10:44 PM    <DIR>          archetypes
04/13/2015  10:44 PM                83 config.toml
04/13/2015  10:44 PM    <DIR>          content
04/13/2015  10:44 PM    <DIR>          data
04/13/2015  10:44 PM    <DIR>          layouts
04/13/2015  10:44 PM    <DIR>          static
               1 File(s)             83 bytes
               7 Dir(s)   6,273,331,200 bytes free
```

### Windowsインストールのトラブルシューティング {#troubleshoot-windows-installation}

よくある問題について、[@dhersam][] が以下の素敵なビデオを作成しました。

{{< youtube c8fJIRNChmU >}}

## Linux

### Snap パッケージ {#snap-package}

[Snap をサポートする Linux ディストリビューション][snaps] のいずれかで、次のコマンドを使用して Sass/SCSS 「拡張版」をインストールできます。

```txt
snap install hugo --channel=extended
```

Sass/SCSS をサポートしない非拡張版をインストールするには、以下のコマンドを実行します。

```txt
snap install hugo
```

この2つを切り替えるには、`snap refresh hugo --channel=extended` または `snap refresh hugo --channel=stable` のどちらかを使用します。

{{% note %}}
Snap 経由でインストールされた Hugo は、Snap の制限とセキュリティモデルにより、ユーザの `$HOME` ディレクトリ --- およびユーザが所有する gvfsマ ウントされたディレクトリ --- 内にのみ書き込みが可能です。より詳細な情報は、[これに関連する GitHub issue](https://github.com/gohugoio/hugo/issues/3143) にもあります。
{{% /note %}}

### Debian と Ubuntu {#debian-and-ubuntu}

[@anthonyfok](https://github.com/anthonyfok) と [Debian Go Packaging Team](https://go-team.pages.debian.net/) の仲間たちは、公式の Hugo [Debian パッケージ](https://packages.debian.org/hugo) を管理しており、これは [Ubuntu](https://packages.ubuntu.com/hugo) と共有して `apt-get` でインストール可能です。

```txt
sudo apt-get install hugo
```

上記のコマンドで何がインストールされるかは、Debian/Ubuntu のバージョンに依存します。 Ubuntu bionic (18.04) では、Sass/SCSS をサポートしない非拡張版がインストールされます。 Ubuntu disco (19.04)では、Sass/SCSS をサポートする拡張版がインストールされます。

[こちら](https://github.com/gcushen/hugo-academic/issues/703) で説明されているように、Debian および Ubuntu 用の Linux パッケージ マネージャーの Hugo は通常、数バージョン遅れているため、このオプションはお勧めしません。

### Arch Linux

Arch Linux [コミュニティ](https://www.archlinux.org/packages/community/x86_64/hugo/) リポジトリから Hugo をインストールすることもできます。Manjaro のような派生版にも適用されます。

```txt
sudo pacman -S hugo
```

### Fedora、Red Hat、CentOS

Fedora では、[Hugo の公式パッケージ](https://packages.fedoraproject.org/pkgs/hugo/hugo) を保守しており、以下のコマンドでインストールできます。

```txt
sudo dnf install hugo
```

最新版については、Fedora Copr の [@daftaupe](https://github.com/daftaupe) が管理している Hugo パッケージが推奨されます。

* <https://copr.fedorainfracloud.org/coprs/daftaupe/hugo/>

[Hugo フォーラムでの関連する議論][redhatforum] を参照してください。

### openSUSE Tumbleweed

openSUSE では、Tumbleweed ローリングリリース ディストリビューション用の [公式パッケージ](https://software.opensuse.org/package/hugo) を管理しており、以下のコマンドでインストールできます。

````txt
sudo zypper install hugo
````

### Solus

Solus は Hugo をパッケージリポジトリに含んでいるので、以下のコマンドでインストールできます。

```txt
sudo eopkg install hugo
```

## OpenBSD

OpenBSD は、Hugo のパッケージを `pkg_add` で提供しています。

```txt
doas pkg_add hugo
```


## Hugo をアップグレードする {#upgrade-hugo}

Hugo のアップグレードは、`PATH` に置いた実行可能ファイルをダウンロードして置き換えるか、Homebrew を使っている場合は `brew upgrade hugo` を実行するだけで簡単にできます。

## 次のステップ {#next-steps}

これで Hugo のインストールが終了したので、[クイックスタート ガイド][quickstart] を読み、 残りのドキュメントを調べてください。質問がある場合は、[Hugo ディスカッション フォーラム][forum] にアクセスして、 Hugo コミュニティに直接質問してください。

[brew]: https://brew.sh/
[macports]: https://www.macports.org/
[Chocolatey]: https://chocolatey.org/
[content]: /content-management/
[@dhersam]: https://github.com/dhersam
[forum]: https://discourse.gohugo.io
[mage]: https://github.com/magefile/mage
[dep]: https://github.com/golang/dep
[highlight shortcode]: /content-management/shortcodes/#highlight
[installgit]: https://git-scm.com/
[GCC]: http://www.mingw.org/
[installgo]: https://go.dev/dl/
[linuxbrew]: https://docs.brew.sh/Homebrew-on-Linux
[quickstart]: /getting-started/quick-start/
[redhatforum]: https://discourse.gohugo.io/t/solved-fedora-copr-repository-out-of-service/2491
[releases]: https://github.com/gohugoio/hugo/releases
[Scoop]: https://scoop.sh/
[snaps]: https://snapcraft.io/docs/installing-snapd
[windowsarch]: https://esupport.trendmicro.com/en-us/home/pages/technical-support/1038680.aspx
[Windows Environment Variables Editor]: https://eveditor.com/
