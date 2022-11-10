---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Formats a string using the standard `fmt.Sprintf` function.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
linktitle: printf
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- printf FORMAT INPUT
title: printf
workson: []
---

See [the go doc](https://golang.org/pkg/fmt/) for additional information.

```
{{ i18n ( printf "combined_%s" $var ) }}
```

```
{{ printf "formatted %.2f" 3.1416 }}
```
