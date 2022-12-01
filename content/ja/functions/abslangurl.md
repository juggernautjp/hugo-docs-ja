---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 多言語対応のサイト構成に従って、正しい言語プレフィックスを持つ絶対 URL を追加します。
draft: false
hugoversion: null
keywords:
- multilingual
- i18n
- urls
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- relLangURL
signature:
- absLangURL INPUT
title: absLangURL
workson: []
---

`absLangURL` と [`relLangURL`](/functions/rellangurl/) はどちらも [`absURL`](/functions/absurl/) と [`relURL`](/functions/relurl) と同じですが、サイトが複数の言語で構成されている場合に正しい言語プレフィックスを追加するようにします。

よって、たとえば、`baseURL` が `https://example.com/hugo/` で、現在の言語が `en` であるサイトがあるとすると、以下のようになります。

```go-html-template
{{ "blog/" | absLangURL }} → "https://example.com/hugo/en/blog/"
{{ "blog/" | relLangURL }} → "/hugo/en/blog/"
```
