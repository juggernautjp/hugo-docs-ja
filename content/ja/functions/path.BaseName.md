---
categories:
- functions
date: "2022-06-04"
deprecated: false
description: BaseName returns the last element of a path, removing the extension if
  present.
draft: true
keywords:
- path
- base
menu:
  docs:
    parent: functions
relatedfuncs:
- path.Base
- path.Clean
- path.Dir
- path.Ext
- path.Join
- path.Split
signature:
- path.BaseName PATH
title: path.BaseName
---

If `PATH` is empty, `.` is returned.

**Note:** On Windows, `PATH` is converted to slash (`/`) separators.

```go-html-template
{{ path.BaseName "a/news.html" }} → "news"
{{ path.BaseName "news.html" }} → "news"
{{ path.BaseName "a/b/c" }} → "c"
{{ path.BaseName "/x/y/z/" }} → "z"
```
