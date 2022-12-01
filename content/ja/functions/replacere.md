---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 正規表現のすべての出現箇所を置換パターンに置き換えます。
draft: false
hugoversion: null
keywords:
- regex
lastmod: "2020-09-07"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- strings.ReplaceRE PATTERN REPLACEMENT INPUT [LIMIT]
- replaceRE PATTERN REPLACEMENT INPUT [LIMIT]
title: replaceRE
workson: []
---

`strings.ReplaceRE` は、正規表現 `PATTERN` にマッチするすべての部分を置換テキスト `REPLACEMENT` に置き換えた `INPUT` のコピーを返します。
オプションの `LIMIT` パラメータで置換の回数を制限できます。

```go-html-template
{{ replaceRE "^https?://([^/]+).*" "$1" "http://gohugo.io/docs" }}` → "gohugo.io"
{{ "http://gohugo.io/docs" | replaceRE "^https?://([^/]+).*" "$1" }}` → "gohugo.io"
{{ replaceRE "a+b" "X" "aabbaabbab" 1 }} → "Xbaabbab"
```

{{% note %}}
Hugo は Go の [正規表現パッケージ](https://golang.org/pkg/regexp/) を使用しています。これは、Perl、Python、その他の言語で使用されている一般的な構文と同じですが、[PCRE](https://www.pcre.org/) [(Perl Compatible Regular Expressions)](https://qualysguard.qualys.com/qwebhelp/jp/fo_portal/module_pc/policies/regular_expression_symbols.htm) のバックグラウンドから来たものとは若干の違いがあります。 完全な構文リストは、[GitHub wiki for re2](https://github.com/google/re2/wiki/Syntax) を参照してください。

RegEx、または少なくとも Go のフレーバーを学んでいる場合は、ブラウザの <https://regex101.com/> ページでパターン マッチングを練習できます。
{{% /note %}}
