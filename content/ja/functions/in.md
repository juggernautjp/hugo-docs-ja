---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Checks if an element is in an array or slice--or a substring in a string---and
  returns a boolean.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
linktitle: null
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- in SET ITEM
title: in
workson: []
---

The elements supported are strings, integers and floats, although only float64 will match as expected.

In addition, `in` can also check if a substring exists in a string.

```
{{ if in .Params.tags "Git" }}Follow me on GitHub!{{ end }}
```


```
{{ if in "this string contains a substring" "substring" }}Substring found!{{ end }}
```
