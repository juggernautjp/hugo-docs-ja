---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Reports if a value is a slice.
draft: true
hugoversion: "0.53"
keywords:
- reflect
- reflection
- kind
lastmod: "2018-11-28"
menu:
  docs:
    parent: functions
publishdate: "2018-11-28"
relatedfuncs:
- reflect.IsMap
signature:
- reflect.IsSlice INPUT
title: reflect.IsSlice
workson: []
---

`reflect.IsSlice` reports if `VALUE` is a slice.  Returns a boolean.

```
{{ reflect.IsSlice (slice 1 2 3) }} → true
{{ reflect.IsSlice "yo" }} → false
```
