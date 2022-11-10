---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns the humanized version of an argument with the first letter capitalized.
draft: true
hugoversion: null
keywords:
- strings
- casing
lastmod: "2017-02-01"
linktitle: null
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- anchorize
signature:
- humanize INPUT
title: humanize
workson: []
---

If the input is either an int64 value or the string representation of an integer, humanize returns the number with the proper ordinal appended.


```
{{humanize "my-first-post"}} → "My first post"
{{humanize "myCamelPost"}} → "My camel post"
{{humanize "52"}} → "52nd"
{{humanize 103}} → "103rd"
```
