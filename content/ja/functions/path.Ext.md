---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Ext returns the file name extension of a path.
draft: true
hugoversion: "0.40"
keywords:
- path
- ext
- extension
lastmod: "2018-11-28"
menu:
  docs:
    parent: functions
publishdate: "2018-11-28"
relatedfuncs:
- path.Base
- path.BaseName
- path.Clean
- path.Dir
- path.Join
- path.Split
signature:
- path.Ext PATH
title: path.Ext
workson: []
---

`path.Ext` returns the file name extension `PATH`.

The extension is the suffix beginning at the final dot in the final slash-separated element `PATH`;
it is empty if there is no dot.

**Note:** On Windows, `PATH` is converted to slash (`/`) separators.

```
{{ path.Ext "a/b/c/news.html" }} → ".html"
```
