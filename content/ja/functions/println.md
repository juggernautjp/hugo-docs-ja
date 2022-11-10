---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Prints the default representation of the given argument using the standard
  `fmt.Print` function and enforces a linebreak.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
linktitle: println
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- println INPUT
title: println
workson: []
---

See [the go doc](https://golang.org/pkg/fmt/) for additional information. `\n` denotes the linebreak but isn't printed in the templates as seen below:

```
{{ println "foo" }} → "foo\n"
```
