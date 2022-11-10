---
aliases: []
categories:
- functions
date: "2020-09-07"
deprecated: false
description: Returns the number of non-overlapping instances of a substring within
  a string.
draft: true
hugoversion: null
keywords:
- count
- counting
- character count
lastmod: "2020-09-07"
menu:
  docs:
    parent: functions
publishdate: "2020-09-07"
relatedfuncs: []
signature:
- strings.Count SUBSTR STRING
title: strings.Count
workson: []
---

{{< new-in "0.74.0" >}}

If `SUBSTR` is an empty string, this function returns 1 plus the number of Unicode code points in `STRING`.

Example|Result
:--|:--
`{{ "aaabaab" \| strings.Count "a" }}`|5
`{{ "aaabaab" \| strings.Count "aa" }}`|2
`{{ "aaabaab" \| strings.Count "aaa" }}`|1
`{{ "aaabaab" \| strings.Count "" }}`|8
