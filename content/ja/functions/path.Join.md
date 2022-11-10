---
categories:
- functions
date: "2018-11-28"
deprecated: false
description: Join path elements into a single path.
draft: true
hugoversion: "0.39"
keywords:
- path
- join
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
- path.Split
signature:
- path.Join ELEMENT...
title: path.Join
workson: []
---

`path.Join` joins path elements into a single path, adding a separating slash if necessary.
All empty strings are ignored.

**Note:** All path elements on Windows are converted to slash ('/') separators.

```
{{ path.Join "partial" "news.html" }} → "partial/news.html"
{{ path.Join "partial/" "news.html" }} → "partial/news.html"
{{ path.Join "foo/baz" "bar" }} → "foo/baz/bar"
```
