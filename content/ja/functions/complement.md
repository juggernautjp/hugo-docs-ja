---
aliases: []
categories:
- functions
date: "2018-11-07"
description: '`collections.Complement` (別名 `complement`) は、他のどのコレクションにもないコレクションの要素を提供します。'
draft: false
hugoversion: "0.51"
keywords:
- collections
- intersect
- union
menu:
  docs:
    parent: functions
signature:
- COLLECTION | complement COLLECTION [COLLECTION]...
title: complement
---

例:

```go-html-template
{{ $pages := site.RegularPages | first 50 }}
{{ $news := where $pages "Type" "news" | first 5 }}
{{ $blog := where $pages "Type" "blog" | first 5 }}
{{ $other := $pages | complement $news $blog | first 10 }}
```

上記は、ページのさまざまな場所のセクション/ボックスにさまざまなページリストを表示する、ホームページの架空の使用例で、
`news` から 5 つ、`blog` から 5 つ、そして表示されていないページのうち 10 ページ 他のリストで、それらを _補完_ するために表示したい場合です。
