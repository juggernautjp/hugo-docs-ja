---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Prints the default representation of the given arguments using the standard
  `fmt.Print` function.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
linktitle: print
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- print INPUT
title: print
workson: []
---

See [the go doc](https://golang.org/pkg/fmt/) for additional information.

```
{{ print "foo" }} → "foo"
{{ print "foo" "bar" }} → "foobar"
{{ print (slice 1 2 3) }} → [1 2 3]
```
