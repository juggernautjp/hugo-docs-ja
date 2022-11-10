---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns the given string with the reserved HTML codes escaped.
draft: true
hugoversion: null
keywords:
- strings
- html
lastmod: "2017-02-01"
linktitle: null
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- htmlUnescape
signature:
- htmlEscape INPUT
title: htmlEscape
workson: []
---

In the result `&` becomes `&amp;` and so on. It escapes only: `<`, `>`, `&`, `'` and `"`.

```
{{ htmlEscape "Hugo & Caddy > WordPress & Apache" }} → "Hugo &amp; Caddy &gt; WordPress &amp; Apache"
```
