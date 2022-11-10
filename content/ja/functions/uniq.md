---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Takes in a slice or array and returns a slice with subsequent duplicate
  elements removed.
draft: true
hugoversion: null
keywords:
- multilingual
- i18n
- urls
lastmod: "2017-02-01"
linktitle: uniq
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- uniq SET
title: uniq
workson: []
---

```
{{ uniq (slice 1 2 3 2) }}
{{ slice 1 2 3 2 | uniq }}
<!-- both return [1 2 3] -->
```
