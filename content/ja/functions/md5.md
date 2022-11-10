---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: hashes the given input and returns its MD5 checksum.
draft: true
hugoversion: null
keywords: []
lastmod: "2017-02-01"
linktitle: md5
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- sha
signature:
- md5 INPUT
title: md5
workson: []
---

```
{{ md5 "Hello world, gophers!" }}
<!-- returns the string "b3029f756f98f79e7f1b7f1d1f0dd53b" -->
```

This can be useful if you want to use [Gravatar](https://en.gravatar.com/) for generating a unique avatar:

```html
<img src="https://www.gravatar.com/avatar/{{ md5 "your@email.com" }}?s=100&d=identicon">
```
