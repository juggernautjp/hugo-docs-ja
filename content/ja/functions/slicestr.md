---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Creates a slice of a half-open range, including start and end indices.
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
- slicestr STRING START [END]
title: slicestr
workson: []
---

For example, 1 and 4 creates a slice including elements 1 through 3.
The `end` index can be omitted; it defaults to the string's length.

* `{{slicestr "BatMan" 3}}` → "Man"
* `{{slicestr "BatMan" 0 3}}` → "Bat"
