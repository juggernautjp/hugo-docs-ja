---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Reports if a value is a map.
draft: true
hugoversion: v0.53
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
- reflect.IsSlice
signature:
- reflect.IsMap INPUT
title: reflect.IsMap
workson: []
---

`reflect.IsMap` reports if `VALUE` is a map.  Returns a boolean.

```
{{ reflect.IsMap (dict "key" "value") }} → true
{{ reflect.IsMap "yo" }} → false
```
