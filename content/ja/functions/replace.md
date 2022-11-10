---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Replaces all occurrences of the search string with the replacement string.
draft: true
hugoversion: null
keywords: []
lastmod: "2020-09-07"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- strings.Replace INPUT OLD NEW [LIMIT]
- replace INPUT OLD NEW [LIMIT]
title: replace
workson: []
---

Replace returns a copy of `INPUT` with all occurrences of `OLD` replaced with `NEW`.
The number of replacements can be limited with an optional `LIMIT` parameter.

```
`{{ replace "Batman and Robin" "Robin" "Catwoman" }}`
→ "Batman and Catwoman"

{{ replace "aabbaabb" "a" "z" 2 }} → "zzbbaabb"
```
