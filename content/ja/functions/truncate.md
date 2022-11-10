---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Truncates a text to a max length without cutting words or leaving unclosed
  HTML tags.
draft: true
hugoversion: 19
keywords:
- strings
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- truncate SIZE INPUT
- truncate SIZE ELLIPSIS INPUT
title: truncate
workson: []
---

Since Go templates are HTML-aware, `truncate` will intelligently handle normal strings vs HTML strings:

```
{{ "<em>Keep my HTML</em>" | safeHTML | truncate 10 }}` → <em>Keep my …</em>`
```

{{% note %}}
If you have a raw string that contains HTML tags you want to remain treated as HTML, you will need to convert the string to HTML using the [`safeHTML` template function](/functions/safehtml) before sending the value to truncate. Otherwise, the HTML tags will be escaped when passed through the `truncate` function.
{{% /note %}}
