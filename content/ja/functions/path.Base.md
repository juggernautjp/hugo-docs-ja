---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Base returns the last element of a path.
draft: true
hugoversion: "0.40"
keywords:
- path
- base
lastmod: "2018-11-28"
menu:
  docs:
    parent: functions
publishdate: "2018-11-28"
relatedfuncs:
- path.BaseName
- path.Clean
- path.Dir
- path.Ext
- path.Join
- path.Split
signature:
- path.Base PATH
title: path.Base
workson: []
---

`path.Base` returns the last element of `PATH`.

If `PATH` is empty, `.` is returned.

**Note:** On Windows, `PATH` is converted to slash (`/`) separators.

```
{{ path.Base "a/news.html" }} → "news.html"
{{ path.Base "news.html" }} → "news.html"
{{ path.Base "a/b/c" }} → "c"
{{ path.Base "/x/y/z/" }} → "z"
```
