---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Dir returns all but the last element of a path.
draft: true
hugoversion: "0.40"
keywords:
- path
- dir
lastmod: "2018-11-28"
menu:
  docs:
    parent: functions
publishdate: "2018-11-28"
relatedfuncs:
- path.Base
- path.BaseName
- path.Clean
- path.Ext
- path.Join
- path.Split
signature:
- path.Dir PATH
title: path.Dir
workson: []
---

`path.Dir` returns all but the last element of `PATH`, typically `PATH`'s directory.

The returned path will never end in a slash.
If `PATH` is empty, `.` is returned.

**Note:** On Windows, `PATH` is converted to slash (`/`) separators.

```
{{ path.Dir "a/news.html" }} → "a"
{{ path.Dir "news.html" }} → "."
{{ path.Dir "a/b/c" }} → "a/b"
{{ path.Dir "/x/y/z" }} → "/x/y"
```
