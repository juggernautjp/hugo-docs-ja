---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Split path immediately following the final slash.
draft: true
hugoversion: "0.39"
keywords:
- path
- split
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
- path.Ext
- path.Join
signature:
- path.Split PATH
title: path.Split
workson: []
---

`path.Split` splits `PATH` immediately following the final slash, separating it into a directory and a base component.

The returned values have the property that `PATH` = `DIR`+`BASE`.
If there is no slash in `PATH`, it returns an empty directory and the base is set to `PATH`.

**Note:** On Windows, `PATH` is converted to slash (`/`) separators.

```
{{ $dirFile := path.Split "a/news.html" }} → $dirFile.Dir → "a/", $dirFile.File → "news.html"
{{ $dirFile := path.Split "news.html" }} → $dirFile.Dir → "", $dirFile.File → "news.html"
{{ $dirFile := path.Split "a/b/c" }} → $dirFile.Dir → "a/b/", $dirFile.File →  "c"
```
