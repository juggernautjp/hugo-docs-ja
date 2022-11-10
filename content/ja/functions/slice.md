---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Creates a slice (array) of all passed arguments.
draft: true
hugoversion: null
keywords:
- slice
- array
- interface
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- slice ITEM...
title: slice
toc: false
workson: []
---

One use case is the concatenation of elements in combination with the [`delimit` function][]:

{{< code file="slice.html" >}}
{{ $sliceOfStrings := slice "foo" "bar" "buzz" }}
<!-- returns the slice [ "foo", "bar", "buzz"] -->
{{ delimit ($sliceOfStrings) ", " }}
<!-- returns the string "foo, bar, buzz" -->
{{< /code >}}


[`delimit` function]: /functions/delimit/
