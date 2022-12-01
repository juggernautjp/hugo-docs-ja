---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 指定された文字列を安全な HTML 属性として宣言します。
draft: false
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- safeHTMLAttr INPUT
title: safeHTMLAttr
workson: []
---

例: サイト全体の `config.toml` が以下のメニューアイテムを含んでいるとします。

{{< code-toggle file="config" >}}
[[menu.main]]
    name = "IRC: #golang at freenode"
    url = "irc://irc.freenode.net/#golang"
{{< /code-toggle >}}

* <span class="bad">`<a href="{{ .URL }}">` &rarr; `<a href="#ZgotmplZ">`</span>
* <span class="good">`<a {{ printf "href=%q" .URL | safeHTMLAttr }}>` &rarr; `<a href="irc://irc.freenode.net/#golang">`</span>
