---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Converts all characters in a string to uppercase
draft: true
hugoversion: null
keywords: []
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- upper INPUT
title: upper
toc: null
workson: []
---

Note that `upper` can be applied in your templates in more than one way:

```go-html-template
{{ upper "BatMan" }} → "BATMAN"
{{ "BatMan" | upper }} → "BATMAN"
```
