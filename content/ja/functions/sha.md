---
aliases:
- sha1
- sha256
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Hashes the given input and returns either an SHA1 or SHA256 checksum.
draft: true
hugoversion: null
keywords:
- sha
- checksum
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- md5
signature:
- sha1 INPUT
- sha256 INPUT
title: sha
workson: []
---

`sha1` hashes the given input and returns its SHA1 checksum.

```
{{ sha1 "Hello world, gophers!" }}
<!-- returns the string "c8b5b0e33d408246e30f53e32b8f7627a7a649d4" -->
```

`sha256` hashes the given input and returns its SHA256 checksum.

```
{{ sha256 "Hello world, gophers!" }}
<!-- returns the string "6ec43b78da9669f50e4e422575c54bf87536954ccd58280219c393f2ce352b46" -->
```
