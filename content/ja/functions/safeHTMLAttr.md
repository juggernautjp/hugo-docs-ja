---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Declares the provided string as a safe HTML attribute.
draft: true
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

Example: Given a site-wide `config.toml` that contains this menu entry:

{{< code-toggle file="config" >}}
[[menu.main]]
    name = "IRC: #golang at freenode"
    url = "irc://irc.freenode.net/#golang"
{{< /code-toggle >}}

* <span class="bad">`<a href="{{ .URL }}">` &rarr; `<a href="#ZgotmplZ">`</span>
* <span class="good">`<a {{ printf "href=%q" .URL | safeHTMLAttr }}>` &rarr; `<a href="irc://irc.freenode.net/#golang">`</span>
