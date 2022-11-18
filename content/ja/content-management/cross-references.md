---
aliases:
- /extras/crossreferences/
categories:
- content management
date: "2017-02-01"
description: ドキュメントへのリンクを作成するためのショートコードです。
draft: false
keywords:
- cross references
- references
- anchors
- urls
lastmod: "2017-03-31"
menu:
  docs:
    parent: content-management
    weight: 100
publishdate: "2017-02-01"
title: リンクとクロスリファレンス
toc: true
weight: 100
---

ショートコードの `ref` と `relref` は、それぞれドキュメントへの絶対パーマリンクと相対パーマリンクを表示します。

## `ref` と `relref` を使用する {#use-ref-and-relref}

```go-html-template
{{</* ref "document" */>}}
{{</* ref "document#anchor" */>}}
{{</* ref "document.md" */>}}
{{</* ref "document.md#anchor" */>}}
{{</* ref "#anchor" */>}}
{{</* ref "/blog/my-post" */>}}
{{</* ref "/blog/my-post.md" */>}}
{{</* relref "document" */>}}
{{</* relref "document.md" */>}}
{{</* relref "#anchor" */>}}
{{</* relref "/blog/my-post.md" */>}}
```

Markdown で `ref` または `relref` を使用してハイパーリンクを生成する方法は、以下の通りです。

```md
[About]({{</* ref "/page/about" */>}} "About Us")
```

`ref` と `relref` ショートコードは、1 つのパラメータを必要とします。それは、コンテンツ ドキュメントへのパスで、ファイル拡張子やアンカーを含むか含まないかです。

**先頭に `/` がないパスは、まず現在のページからの相対パスが解決され、次にサイトの残りの部分からの相対パスが解決されます。

Hugo は、ドキュメントを一意に解決できない場合にエラーや警告を発します。エラーの動作は設定可能です。下記を参照してください。

### 他言語版にリンクする {#link-to-another-language-version}

別の言語版のドキュメントにリンクする場合は、以下の構文を使用します。

```go-html-template
{{</* relref path="document.md" lang="ja" */>}}
```

### 別の出力形式を取得する {#get-another-output-format}

ドキュメントの別の出力形式にリンクするには、以下の構文を使用します。

```go-html-template
{{</* relref path="document.md" outputFormat="rss" */>}}
```

### 見出し ID {#heading-ids}

Markdown ドキュメント タイプを使用する場合、Hugo はページのすべての見出しの要素 ID を生成します。 たとえば、

```md
## Reference
```

は、以下の HTML を生成します。

```html
<h2 id="reference">Reference</h2>
```

`ref` または `relref` ショートコードを使用する場合、パスに ID を追加して、見出しへのパーマリンクを取得します。

```go-html-template
{{</* ref "document.md#reference" */>}}
{{</* relref "document.md#reference" */>}}
```

属性を含めてカスタムの見出し ID を生成します。 たとえば、

```md
## Reference A {#foo}
## Reference B {id="bar"}
```

は、以下の HTML を生成します。

```html
<h2 id="foo">Reference A</h2>
<h2 id="bar">Reference B</h2>
```

同じ見出しがページに複数回表示される場合、Hugo は一意の要素 ID を生成します。 たとえば、

```md
## Reference
## Reference
## Reference
```

は、以下の HTML を生成します。

```html
<h2 id="reference">Reference</h2>
<h2 id="reference-1">Reference</h2>
<h2 id="reference-2">Reference</h2>
```

## Ref と RelRef の設定 {#ref-and-relref-configuration}

Hugo 0.45 以降では、`config.toml` で動作を設定できます。

refLinksErrorLevel ("ERROR")
: ページリンクの解決に `ref` や `relref` を使用していて、リンクが解決できなかった場合に、このログレベルでログに記録されます。有効な値は `ERROR` (デフォルト) または `WARNING` (警告) です。 `ERROR` が指定された場合は、ビルドに失敗します (`exit -1`).

refLinksNotFoundURL
: `ref` または `relref` でページ参照が見つからない場合に、プレースホルダとして使用する URL で、そのまま使用されます。


[lists]: /templates/lists/
[output formats]: /templates/output-formats/
[shortcode]: /content-management/shortcodes/
