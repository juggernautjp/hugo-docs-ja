---
aliases: []
categories:
- functions
date: "2018-11-07"
description: '`collections.SymDiff` (alias `symdiff`) returns the symmetric difference
  of two collections.'
draft: true
hugoversion: "0.51"
keywords:
- collections
- intersect
- union
- complement
menu:
  docs:
    parent: functions
signature:
- COLLECTION | symdiff COLLECTION
title: symdiff
---

Example:

```go-html-template
{{ slice 1 2 3 | symdiff (slice 3 4) }}
```

The above will print `[1 2 4]`.

Also see https://en.wikipedia.org/wiki/Symmetric_difference
