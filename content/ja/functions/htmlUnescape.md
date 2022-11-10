---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns the given string with HTML escape codes un-escaped.
draft: true
hugoversion: null
keywords: []
lastmod: "2017-02-01"
linktitle: htmlUnescape
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- htmlEscape
signature:
- htmlUnescape INPUT
title: htmlUnescape
workson: []
---

`htmlUnescape` returns the given string with HTML escape codes un-escaped.

Remember to pass the output of this to `safeHTML` if fully un-escaped characters are desired. Otherwise, the output will be escaped again as normal.

```
{{ htmlUnescape "Hugo &amp; Caddy &gt; WordPress &amp; Apache" }} → "Hugo & Caddy > WordPress & Apache"
```
