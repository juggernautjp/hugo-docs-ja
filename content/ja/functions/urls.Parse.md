---
aliases: []
categories:
- functions
date: "2017-09-25"
deprecated: false
description: Parse parses a given url, which may be relative or absolute, into a URL
  structure.
draft: true
hugoversion: null
keywords:
- urls
lastmod: "2017-09-25"
menu:
  docs:
    parent: functions
publishdate: "2017-09-25"
signature:
- urls.Parse URL
title: urls.Parse
workson: []
---

`urls.Parse` takes a url as input


```go-html-template
{{ $url := urls.Parse "http://www.gohugo.io" }}
```

and returns a [URL](https://godoc.org/net/url#URL) structure. The struct fields are accessed via the `.` notation:

```go-html-template
{{ $url.Scheme }} → "http"
{{ $url.Host }} → "www.gohugo.io"
```
