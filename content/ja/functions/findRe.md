---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 正規表現にマッチする文字列のリストを返します。
draft: false
hugoversion: null
keywords:
- regex
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- findRE PATTERN INPUT [LIMIT]
title: findRE
workson: []
---

デフォルトでは、すべてのマッチが含まれます。マッチの数は、オプションの第 3 パラメータで制限することができます。

以下の例では、コンテンツに含まれるすべての第 2 レベルのヘッダー (`<h2>`) のリストを返します。

```go-html-template
{{ findRE "<h2.*?>(.|\n)*?</h2>" .Content }}
```

3 番目のパラメータで、リスト内のマッチの数を制限できます。 以下の例は、返される値を 1 つのマッチしたものだけに制限する方法を示しています (マッチする部分文字列がない場合は、どれにもマッチしません)。

```go-html-template
{{ findRE "<h2.*?>(.|\n)*?</h2>" .Content 1 }}
    <!-- returns ["<h2 id="#foo">Foo</h2>"] -->
```

{{% note %}}
Hugo は Go の [正規表現パッケージ](https://golang.org/pkg/regexp/) を使用しています。これは、Perl、Python、その他の言語で使用されている一般的な構文と同じですが、[PCRE](https://www.pcre.org/) [(Perl Compatible Regular Expressions)](https://qualysguard.qualys.com/qwebhelp/jp/fo_portal/module_pc/policies/regular_expression_symbols.htm) のバックグラウンドから来たものとは若干の違いがあります。 完全な構文リストは、[GitHub wiki for re2](https://github.com/google/re2/wiki/Syntax) を参照してください。

RegEx、または少なくとも Go のフレーバーを学んでいる場合は、ブラウザの <https://regex101.com/> ページでパターン マッチングを練習できます。
{{% /note %}}

[partials]: /templates/partials/
[`plainify`]: /functions/plainify/
[toc]: /content-management/toc/
[`urlize`]: /functions/urlize
