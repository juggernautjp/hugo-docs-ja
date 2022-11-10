---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Strips any HTML and returns the plain text version of the provided string.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-04-30"
linktitle: plainify
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- jsonify
signature:
- plainify INPUT
title: plainify
workson: []
---

```
{{ "<b>BatMan</b>" | plainify }} → "BatMan"
```

See also the `.PlainWords`, `.Plain`, and `.RawContent` [page variables][pagevars].

[pagevars]: /variables/page/
