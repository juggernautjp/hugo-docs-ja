---
aliases: []
categories:
- functions
date: "2018-09-14"
description: '`append` appends one or more values to a slice and returns the resulting
  slice.'
draft: true
hugoversion: "0.49"
keywords:
- collections
menu:
  docs:
    parent: functions
relatedfuncs:
- last
- first
- where
- slice
signature:
- COLLECTION | append VALUE [VALUE]...
- COLLECTION | append COLLECTION
title: append
workson: []
---

An example appending single values:

```go-html-template
{{ $s := slice "a" "b" "c" }}
{{ $s = $s | append "d" "e" }}
{{/* $s now contains a []string with elements "a", "b", "c", "d", and "e" */}}

```

The same example appending a slice to a slice:

```go-html-template
{{ $s := slice "a" "b" "c" }}
{{ $s = $s | append (slice "d" "e") }}
```

The `append` function works for all types, including `Pages`.
