---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Encodes a given object to JSON.
draft: true
hugoversion: null
keywords:
- strings
- json
lastmod: "2020-04-13"
linktitle: jsonify
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- plainify
signature:
- jsonify INPUT
- jsonify OPTIONS INPUT
title: jsonify
workson: []
---

Jsonify encodes a given object to JSON.

To customize the printing of the JSON, pass a dictionary of options as the first
argument.  Supported options are "prefix" and "indent".  Each JSON element in
the output will begin on a new line beginning with *prefix* followed by one or
more copies of *indent* according to the indentation nesting.


```
{{ dict "title" .Title "content" .Plain | jsonify }}
{{ dict "title" .Title "content" .Plain | jsonify (dict "indent" "  ") }}
{{ dict "title" .Title "content" .Plain | jsonify (dict "prefix" " " "indent" "  ") }}
```

## Jsonify options

indent ("")
: Indentation to use.

prefix ("")
: Indentation prefix.

noHTMLEscape (false)
: Disable escaping of problematic HTML characters inside JSON quoted strings. The default behavior is to escape &, <, and > to \u0026, \u003c, and \u003e to avoid certain safety problems that can arise when embedding JSON in HTML.

See also the `.PlainWords`, `.Plain`, and `.RawContent` [page variables][pagevars].

[pagevars]: /variables/page/
