---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Determines the number of runes in a string excluding any whitespace.
draft: true
hugoversion: null
keywords:
- counting
- word count
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- countrunes INPUT
title: countrunes
workson: []
---

In contrast with `countwords` function, which counts every word in a string, the `countrunes` function determines the number of runes in the content and excludes any whitespace. This has specific utility if you are dealing with CJK-like languages.

```
{{ "Hello, 世界" | countrunes }}
<!-- outputs a content length of 8 runes. -->
```

[pagevars]: /variables/page/
