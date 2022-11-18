---
aliases:
- /layouts/introduction/
- /layout/introduction/
- /templates/go-templates/
categories:
- templates
- fundamentals
date: "2017-02-01"
description: Hugo はテンプレート作成の基礎として、Go の `html/template` ライブラリと `text/template` ライブラリを使用します。
draft: false
keywords:
- go
lastmod: "2022-09-20"
linktitle: テンプレート
menu:
  docs:
    parent: templates
    weight: 10
publishdate: "2017-02-01"
sections_weight: 10
title: Hugo テンプレート入門
toc: true
weight: 10
---

{{% note %}}
以下は、Go テンプレートについての入門書です。 Go テンプレートについての詳細については、公式の [Go ドキュメント](https://golang.org/pkg/text/template/) を確認してださい。
{{% /note %}}

Go テンプレートは、最も基本的なロジックのみがテンプレートまたはビュー層に属するという信念に基づき、極めてシンプルなテンプレート言語を提供します。

## 基本構文 {#basic-syntax}

Go テンプレートは、[変数][variables] と [関数][functions] が追加された HTML ファイルです。 Go テンプレートの変数と関数は `{{ }}` 内でアクセスできます。

### 定義済み変数にアクセスする {#access-a-predefined-variable}

_定義済み変数_ とは、現在のスコープに既に存在する変数 (以下の [変数]({{< relref "#variables" >}}) セクションの `.Title` の例のように)、またはカスタム変数 (同じセクションの `$address` の例のように) である可能性があります。

```go-html-template
{{ .Title }}
{{ $address }}
```

関数のパラメーターはスペースで区切られます。 一般的な構文は、以下の通りです。

```go-html-template
{{ FUNCTION ARG1 ARG2 .. }}
```

以下の例では、`1` と `2` を入力として `add` 関数を呼び出しています。

```go-html-template
{{ add 1 2 }}
```

#### メソッドとフィールドはドット記法でアクセスする {#methods-and-fields-are-accessed-via-dot-notation}

コンテンツの [フロントマター][front matter] に定義されているページパラメーター `bar` にアクセスします。

```go-html-template
{{ .Params.bar }}
```

#### 括弧を使用してアイテムをグループ化できる {#parentheses-can-be-used-to-group-items-together}

```go-html-template
{{ if or (isset .Params "alt") (isset .Params "caption") }} Caption {{ end }}
```

#### 1 つのステートメントを複数行に分割できる {#a-single-statement-can-be-split-over-multiple-lines}

```go-html-template
{{ if or
  (isset .Params "alt")
  (isset .Params "caption")
}}
```

#### Raw (生) 文字列リテラルには改行を含めることができる {#raw-string-literals-can-include-newlines}

```go-html-template
{{ $msg := `Line one.
Line two.` }}
```

## 変数 {#variables}

各 Go テンプレートはデータオブジェクトを取得します。 Hugo では、各テンプレートに `Page` が渡されます。 以下の例では、`.Title` はその [`Page` 変数][pagevars] でアクセス可能な要素の 1 つです。

`Page` がテンプレートのデフォルトスコープであるため、現在のスコープ (`.` -- "**ドット**") にある `Title` 要素には、以下のようなドットプレフィックス (`.Title`) で簡単にアクセスできます。

```go-html-template
<title>{{ .Title }}</title>
```

また、値はカスタム変数に保存し、後で参照することもできます。

{{% note %}}
The custom variables need to be prefixed with `$`.
{{% /note %}}

```go-html-template
{{ $address := "123 Main St." }}
{{ $address }}
```

変数は `=` 演算子を用いて再定義できます。以下の例では、ホームページに "Var is Hugo Home" と表示し、他のすべてのページには "Var is Hugo Page" と表示します。

```go-html-template
{{ $var := "Hugo Page" }}
{{ if .IsHome }}
    {{ $var = "Hugo Home" }}
{{ end }}
Var is {{ $var }}
```

## 関数 {#functions}

Go テンプレートはいくつかの基本的な関数を備えているだけでなく、アプリケーションが元のセットを拡張するためのメカニズムも提供します。

[Hugo テンプレート関数][functions] は、Web サイトを構築するために必要な機能を追加します。関数を呼び出すには、関数の名前に続けて、必要なパラメーターをスペースで区切って指定します。テンプレート関数は、Hugo を再コンパイルしないと追加できません。

### 例 1: 数字の足し算 {#example-1-adding-numbers}

```go-html-template
{{ add 1 2 }}
<!-- prints 3 -->
```

### 例 2：数値の比較 {#example-2-comparing-numbers}

```go-html-template
{{ lt 1 2 }}
<!-- prints true (i.e., since 1 is less than 2) -->
```

どちらの例も、Go テンプレートの [math][math] 関数を使用していることに注意してください。

{{% note "Additional Boolean Operators" %}}
[Go テンプレートのドキュメント](https://golang.org/pkg/text/template/#hdr-Functions) には、Hugo のドキュメントに掲載されている以外にも多くのブール演算子があります。
{{% /note %}}

## インクルードする (含める) {#includes}

別のテンプレートを含める場合は、アクセスする必要があるデータを渡す必要があります。

{{% note %}}
現在のコンテキストを伝えるために、末尾に **ドット** を含めることを忘れないでください。
{{% /note %}}

テンプレートの場所は、常に Hugo 内の `layouts/` ディレクトリから始まります。

### パーシャル (部分テンプレート) {#partial}

[`partial`][partials] 関数は、構文 `{{ partial "<PATH>/<PARTIAL>.<EXTENSION>" . }}` を使用して _部分_ テンプレートをインクルードするために使用されます。

以下は、`layouts/partials/header.html` パーシャルをインクルードする例です。

```go-html-template
{{ partial "header.html" . }}
```

### テンプレート {#template}

Hugo のかなり古いバージョンでは、 `template` 関数は _部分_ テンプレートをインクルードするために使用されていました。今は、[_部分_ テンプレート][internal templates] を呼び出すのにのみ有効です。この構文は、 `{{ template "_internal/<TEMPLATE>.<EXTENSION>" . }}` です。

{{% note %}}
利用可能な **内部** テンプレートは、 [ここ](https://github.com/gohugoio/hugo/tree/master/tpl/tplimpl/embedded/templates) で確認できます。
{{% /note %}}

以下は、内部テンプレート `opengraph.html` をインクルードする例です。

```go-html-template
{{ template "_internal/opengraph.html" . }}
```

## ロジック {#logic}

Go テンプレートは、最も基本的な反復処理と条件分岐のロジックを提供します。

### 反復処理 {#iteration}

Go テンプレートは、`range` を多用して _map_、_array_、または _slice_ を反復処理します。 以下は、`range` の使用方法のさまざまな例です。

#### 例 1: コンテキストの使用 (`.`) {#eExample-1-using-context}

```go-html-template
{{ range $array }}
    {{ . }} <!-- The . represents an element in $array -->
{{ end }}
```

#### 例 2: 配列要素の値を変数名で宣言する {example-2-declaring-a-variable-name-for-an-array-elements-value}

```go-html-template
{{ range $elem_val := $array }}
    {{ $elem_val }}
{{ end }}
```

#### 例 3: 配列要素のインデックス _と_ 値を変数名で宣言する {example-3-declaring-variable-names-for-an-array-elements-index-and-value}

配列またはスライスの場合、最初に宣言された変数が各要素のインデックスにマップされます。

```go-html-template
{{ range $elem_index, $elem_val := $array }}
   {{ $elem_index }} -- {{ $elem_val }}
{{ end }}
```

#### 例 4: マップ要素のキー _と_ 値を変数名で宣言する {#example-4-declaring-variable-names-for-a-map-elements-key-and-value}

マップの場合、最初に宣言された変数が各マップ要素のキーにマップされます。

```go-html-template
{{ range $elem_key, $elem_val := $map }}
   {{ $elem_key }} -- {{ $elem_val }}
{{ end }}
```

#### 例 5: 空の _マップ_、_配列_ または _スライス_ の条件付き {#example-5-conditional-on-empty-map-array-or-slice}

`range` に渡された _map_、_array_、または _slice_ の長さがゼロの場合、else 文が評価されます。

```go-html-template
{{ range $array }}
    {{ . }}
{{else}}
    <!-- This is only evaluated if $array is empty -->
{{ end }}
```

### 条件分岐 {#conditionals}

`if`、`else`、`with`、`or`、`and`、`not` は、 Go テンプレートで条件分岐を扱うためのフレームワークを提供します。 `range` と同様に、 `if` と `with` 文は `{{ end }}` で閉じます。

Go テンプレートは、以下の値を **false** として扱います。

- `false` (boolean)
- 0 (integer)
- 長さゼロの配列、スライス、マップ、または文字列

#### 例 1: `with` {#example-1-with}

`with` を使って「何かあったらこうする」というような文を書くのが一般的です。

{{% note %}}
`with` は、そのスコープ内でコンテキスト `.` を再バインドします (`range` と同様)。
{{% /note %}}

変数が存在しない場合や、上記で説明したように "false" と評価された場合は、ブロックをスキップします。

```go-html-template
{{ with .Params.title }}
    <h4>{{ . }}</h4>
{{ end }}
```

#### 例 2: `with` .. `else` {#example-2-with-else}

以下のスニペットは、設定されている場合は "description" フロントマター パラメータの値を使用し、設定されていない場合はデフォルトの `.Summary` [ページ変数][pagevars] を使用します。

```go-html-template
{{ with .Param "description" }}
    {{ . }}
{{ else }}
    {{ .Summary }}
{{ end }}
```

詳細は、[`.Param` 関数][param] を参照してください。

#### 例 3: `if` {#example-3-if}

`with` の別の (そしてより冗長な) 書き方は、`if` を使用することです。 ここで、`.` はリバウンドしません。

以下の例は、「例 1」を `if` を使って書き直したものです。

```go-html-template
{{ if isset .Params "title" }}
    <h4>{{ index .Params "title" }}</h4>
{{ end }}
```

#### 例 4: `if` .. `else` {#example-4-if-else}

以下の例は、「例 2」を `if` ... `else` で書き換え、代わりに [`isset` 関数][isset] + `.Params` 変数 (`.Param` **関数**][param] とは異なる) を使用した例です。

```go-html-template
{{ if (isset .Params "description") }}
    {{ index .Params "description" }}
{{ else }}
    {{ .Summary }}
{{ end }}
```

#### 例 5: `if` .. `else if` .. `else` {#example-5-if-else-if-else}

`with` とは異なり、 `if` には `else if` 節を含めることもできます。

```go-html-template
{{ if (isset .Params "description") }}
    {{ index .Params "description" }}
{{ else if (isset .Params "summary") }}
    {{ index .Params "summary" }}
{{ else }}
    {{ .Summary }}
{{ end }}
```

#### 例 6: `and` および `or` {#example-6-and-or}

```go-html-template
{{ if (and (or (isset .Params "title") (isset .Params "caption")) (isset .Params "attr")) }}
```

## パイプ {#pipes}

Go テンプレートの最も強力なコンポーネントの 1 つは、アクションを次々に積み重ねることができることです。これはパイプを使うことで実現されます。 Unix のパイプから借りたもので、コンセプトは単純です。つまり、各パイプラインの出力が次のパイプの入力になります。

Go テンプレートの構文は非常に単純であるため、関数呼び出しを連鎖させるにはパイプが不可欠です。 パイプの制限の 1 つは、単一の値しか扱えず、その値が次のパイプラインの最後のパラメータになることです。

いくつかの簡単な例で、パイプの使用方法を説明します。

### 例 1: `shuffle` {#example-1-shuffle}

以下の 2 つの例は、機能的に同じです。

```go-html-template
{{ shuffle (seq 1 5) }}
```

```go-html-template
{{ (seq 1 5) | shuffle }}
```

### 例 2: `index` {#example-2-index}

以下は "disqus_url" というページパラメータにアクセスし、HTML をエスケープしています。この例では、Go テンプレートに組み込まれている [`index` 関数](/functions/index-function/) も使用しています。

```go-html-template
{{ index .Params "disqus_url" | html }}
```

### 例 2: `or` with `isset` {#example-3-or-with-isset}

```go-html-template
{{ if or (or (isset .Params "title") (isset .Params "caption")) (isset .Params "attr") }}
Stuff Here
{{ end }}
```

上記は、以下のように書き換えることができます。

```go-html-template
{{ if isset .Params "caption" | or isset .Params "title" | or isset .Params "attr" }}
Stuff Here
{{ end }}
```

## コンテキスト (別名「ドット」) {#the-dot}

The most easily overlooked concept to understand about Go Templates is that `{{ . }}` always refers to the **current context**.

- In the top level of your template, this will be the data set made available to it.
- Inside an iteration, however, it will have the value of the current item in the loop; i.e., `{{ . }}` will no longer refer to the data available to the entire page.

If you need to access page-level data (e.g., page params set in front matter) from within the loop, you will likely want to do one of the following:

### 1. Define a Variable Independent of Context

The following shows how to define a variable independent of the context.

{{< code file="tags-range-with-page-variable.html" >}}
{{ $title := .Site.Title }}
<ul>
{{ range .Params.tags }}
    <li>
        <a href="/tags/{{ . | urlize }}">{{ . }}</a>
        - {{ $title }}
    </li>
{{ end }}
</ul>
{{< /code >}}

{{% note %}}
Notice how once we have entered the loop (i.e. `range`), the value of `{{ . }}` has changed. We have defined a variable outside the loop (`{{$title}}`) that we've assigned a value so that we have access to the value from within the loop as well.
{{% /note %}}

### 2. Use `$.` to Access the Global Context

`$` has special significance in your templates. `$` is set to the starting value of `.` ("the dot") by default. This is a [documented feature of Go text/template][dotdoc]. This means you have access to the global context from anywhere. Here is an equivalent example of the preceding code block but now using `$` to grab `.Site.Title` from the global context:

{{< code file="range-through-tags-w-global.html" >}}
<ul>
{{ range .Params.tags }}
  <li>
    <a href="/tags/{{ . | urlize }}">{{ . }}</a>
            - {{ $.Site.Title }}
  </li>
{{ end }}
</ul>
{{< /code >}}

{{% warning "Don't Redefine the Dot" %}}
The built-in magic of `$` would cease to work if someone were to mischievously redefine the special character; e.g. `{{ $ := .Site }}`. *Don't do it.* You may, of course, recover from this mischief by using `{{ $ := . }}` in a global context to reset `$` to its default value.
{{% /warning %}}

## Whitespace

Go 1.6 includes the ability to trim the whitespace from either side of a Go tag by including a hyphen (`-`) and space immediately beside the corresponding `{{` or `}}` delimiter.

For instance, the following Go Template will include the newlines and horizontal tab in its HTML output:

```go-html-template
<div>
  {{ .Title }}
</div>
```

Which will output:

```html
<div>
  Hello, World!
</div>
```

Leveraging the `-` in the following example will remove the extra white space surrounding the `.Title` variable and remove the newline:

```go-html-template
<div>
  {{- .Title -}}
</div>
```

Which then outputs:

```html
<div>Hello, World!</div>
```

Go considers the following characters _whitespace_:

* <kbd>space</kbd>
* horizontal <kbd>tab</kbd>
* carriage <kbd>return</kbd>
* newline

## Comments

In order to keep your templates organized and share information throughout your team, you may want to add comments to your templates. There are two ways to do that with Hugo.

### Go Templates comments

Go Templates support `{{/*` and `*/}}` to open and close a comment block. Nothing within that block will be rendered.

For example:

```go-html-template
Bonsoir, {{/* {{ add 0 + 2 }} */}}Eliott.
```

Will render `Bonsoir, Eliott.`, and not care about the syntax error (`add 0 + 2`) in the comment block.

### HTML comments

If you need to produce HTML comments from your templates, take a look at the [Internet Explorer conditional comments]({{< relref "introduction.md#ie-conditional-comments" >}}) example. If you need variables to construct such HTML comments, just pipe `printf` to `safeHTML`. For example:

```go-html-template
{{ printf "<!-- Our website is named: %s -->" .Site.Title | safeHTML }}
```

#### HTML comments containing Go Templates

HTML comments are by default stripped, but their content is still evaluated. That means that although the HTML comment will never render any content to the final HTML pages, code contained within the comment may fail the build process.

{{% note %}}
Do **not** try to comment out Go Template code using HTML comments.
{{% /note %}}

```go-html-template
<!-- {{ $author := "Emma Goldman" }} was a great woman. -->
{{ $author }}
```

The templating engine will strip the content within the HTML comment, but will first evaluate any Go Template code if present within. So the above example will render `Emma Goldman`, as the `$author` variable got evaluated in the HTML comment. But the build would have failed if that code in the HTML comment had an error.

## Hugo Parameters

Hugo provides the option of passing values to your template layer through your [site configuration][config] (i.e. for site-wide values) or through the metadata of each specific piece of content (i.e. the [front matter][]). You can define any values of any type and use them however you want in your templates, as long as the values are supported by the [front matter format]({{< ref "front-matter.md#front-matter-formats" >}}).

## Use Content (`Page`) Parameters

You can provide variables to be used by templates in individual content's [front matter][].

An example of this is used in the Hugo docs. Most of the pages benefit from having the table of contents provided, but sometimes the table of contents doesn't make a lot of sense. We've defined a `notoc` variable in our front matter that will prevent a table of contents from rendering when specifically set to `true`.

Here is the example front matter (YAML):

```yml
---
title: Roadmap
lastmod: 2017-03-05
date: 2013-11-18
notoc: true
---
```

Here is an example of corresponding code that could be used inside a `toc.html` [partial template][partials]:

{{< code file="layouts/partials/toc.html" download="toc.html" >}}
{{ if not .Params.notoc }}
<aside>
  <header>
    <a href="#{{.Title | urlize}}">
    <h3>{{.Title}}</h3>
    </a>
  </header>
  {{.TableOfContents}}
</aside>
<a href="#" id="toc-toggle"></a>
{{ end }}
{{< /code >}}

We want the *default* behavior to be for pages to include a TOC unless otherwise specified. This template checks to make sure that the `notoc:` field in this page's front matter is not `true`.

## Use Site Configuration Parameters

You can arbitrarily define as many site-level parameters as you want in your [site's configuration file][config]. These parameters are globally available in your templates.

For instance, you might declare the following:

{{< code-toggle file="config" >}}
params:
  copyrighthtml: "Copyright &#xA9; 2017 John Doe. All Rights Reserved."
  twitteruser: "spf13"
  sidebarrecentlimit: 5
{{< /code >}}

Within a footer layout, you might then declare a `<footer>` that is only rendered if the `copyrighthtml` parameter is provided. If it *is* provided, you will then need to declare the string is safe to use via the [`safeHTML` function][safehtml] so that the HTML entity is not escaped again. This would let you easily update just your top-level config file each January 1st, instead of hunting through your templates.

```go-html-template
{{ if .Site.Params.copyrighthtml }}
    <footer>
        <div class="text-center">{{.Site.Params.CopyrightHTML | safeHTML}}</div>
    </footer>
{{ end }}
```

An alternative way of writing the "`if`" and then referencing the same value is to use [`with`][with] instead. `with` rebinds the context (`.`) within its scope and skips the block if the variable is absent:

{{< code file="layouts/partials/twitter.html" >}}
{{ with .Site.Params.twitteruser }}
    <div>
        <a href="https://twitter.com/{{.}}" rel="author">
        <img src="/images/twitter.png" width="48" height="48" title="Twitter: {{.}}" alt="Twitter"></a>
    </div>
{{ end }}
{{< /code >}}

Finally, you can pull "magic constants" out of your layouts as well. The following uses the [`first`][first] function, as well as the [`.RelPermalink`][relpermalink] page variable and the [`.Site.Pages`][sitevars] site variable.

```go-html-template
<nav>
  <h1>Recent Posts</h1>
  <ul>
  {{- range first .Site.Params.SidebarRecentLimit .Site.Pages -}}
      <li><a href="{{.RelPermalink}}">{{.Title}}</a></li>
  {{- end -}}
  </ul>
</nav>
```

## Example: Show Future Events

Given the following content structure and [front matter]:

```text
content/
└── events/
    ├── event-1.md
    ├── event-2.md
    └── event-3.md
```

{{< code-toggle file="content/events/event-1.md" copy="false" >}}
title = 'Event 1'
date = 2021-12-06T10:37:16-08:00
draft = false
start_date = 2021-12-05T09:00:00-08:00
end_date = 2021-12-05T11:00:00-08:00
{{< /code-toggle >}}

This [partial template][partials] renders future events:

{{< code file="layouts/partials/future-events.html" >}}
<h2>Future Events</h2>
<ul>
  {{ range where site.RegularPages "Type" "events" }}
    {{ if gt (.Params.start_date | time.AsTime) now }}
      {{ $startDate := .Params.start_date | time.Format ":date_medium" }}
      <li>
        <a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a> - {{ $startDate }}
      </li>
    {{ end }}
  {{ end }}
</ul>
{{< /code >}}

If you restrict front matter to the TOML format, and omit quotation marks surrounding date fields, you can perform date comparisons without casting.

{{< code file="layouts/partials/future-events.html" >}}
<h2>Future Events</h2>
<ul>
  {{ range where (where site.RegularPages "Type" "events") "Params.start_date" "gt" now }}
    {{ $startDate := .Params.start_date | time.Format ":date_medium" }}
    <li>
      <a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a> - {{ $startDate }}
    </li>
  {{ end }}
</ul>
{{< /code >}}

[config]: {{< relref "getting-started/configuration" >}}
[dotdoc]: https://golang.org/pkg/text/template/#hdr-Variables
[first]: {{< relref "functions/first" >}}
[front matter]: {{< relref "content-management/front-matter" >}}
[functions]: {{< relref "functions" >}}
[internal templates]: {{< relref "templates/internal" >}}
[isset]: {{< relref "functions/isset" >}}
[math]: {{< relref "functions/math" >}}
[pagevars]: {{< relref "variables/page" >}}
[param]: {{< relref "functions/param" >}}
[partials]: {{< relref "templates/partials" >}}
[relpermalink]: {{< relref "variables/page#page-variables" >}}
[safehtml]: {{< relref "functions/safehtml" >}}
[sitevars]: {{< relref "variables/site" >}}
[variables]: {{< relref "variables" >}}
[with]: {{< relref "functions/with" >}}
