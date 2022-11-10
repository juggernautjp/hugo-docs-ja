---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Extracts parts of a string from a specified character's position and
  returns the specified number of characters.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- substr STRING START [LENGTH]
title: substr
workson: []
---

It normally takes two parameters: `start` and `length`. It can also take one parameter: `start`, i.e. `length` is omitted, in which case the substring starting from start until the end of the string will be returned.

To extract characters from the end of the string, use a negative start number.

If `length` is given and is negative, that number of characters will be omitted from the end of string.

```
{{ substr "abcdef" 0 }} → "abcdef"
{{ substr "abcdef" 1 }} → "bcdef"

{{ substr "abcdef" 0 1 }} → "a"
{{ substr "abcdef" 1 1 }} → "b"

{{ substr "abcdef" 0 -1 }} → "abcde"
{{ substr "abcdef" 1 -1 }} → "bcde"

{{ substr "abcdef" -1 }} → "f"
{{ substr "abcdef" -2 }} → "ef"

{{ substr "abcdef" -1 1 }} → "f"
{{ substr "abcdef" -2 1 }} → "e"

{{ substr "abcdef" -3 -1 }} → "de"
{{ substr "abcdef" -3 -2 }} → "d"
```
