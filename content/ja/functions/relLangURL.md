---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 多言語対応のサイト設定に従って、適切な言語プレフィックスを持つ相対 URL を追加します。
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
relatedfuncs: []
signature:
- relLangURL INPUT
title: relLangURL
workson: []
---

`absLangURL` および `relLangURL` 関数は、それらの [`absURL`](/functions/absurl/) および [`relURL`](/functions/relurl/) に類似していますが、サイトが複数の言語で構成されている場合に正しい言語プレフィックスを追加します (詳細は、[「言語を設定する」][multiliconfig] を参照してください)。

たとえば、`baseURL` が `https://example.com/hugo/` に設定され、現在の言語が `en` であるサイトがあるとすると、以下のようになります。

```go-html-template
{{ "blog/" | absLangURL }} → "https://example.com/hugo/en/blog/"
{{ "blog/" | relLangURL }} → "/hugo/en/blog/"
```

[multiliconfig]: /content-management/multilingual/#configure-languages
