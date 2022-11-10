---
aliases: []
categories:
- functions
date: "2018-06-01"
deprecated: false
description: Determines the number of runes in a string.
draft: true
hugoversion: null
keywords:
- counting
- character count
- length
- rune length
- rune count
lastmod: "2018-06-01"
menu:
  docs:
    parent: functions
publishdate: "2018-06-01"
relatedfuncs:
- len
- countrunes
signature:
- strings.RuneCount INPUT
title: strings.RuneCount
workson: []
---

In contrast with `strings.CountRunes` function, which strips HTML and whitespace before counting runes, `strings.RuneCount` simply counts all the runes in a string. It relies on the Go [`utf8.RuneCountInString`] function.

```
{{ "Hello, 世界" | strings.RuneCount }}
<!-- outputs a content length of 9 runes. -->
```

[`utf8.RuneCount`]: https://golang.org/pkg/unicode/utf8/#RuneCount
