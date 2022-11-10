---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: slices an array to only the last <em>N</em>th elements.
draft: true
hugoversion: null
keywords: []
lastmod: "2017-02-01"
linktitle: last
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- last INDEX COLLECTION
title: last
toc: null
workson:
- lists
- taxonomies
- terms
- groups
---

```
{{ range last 10 .Pages }}
    {{ .Render "summary" }}
{{ end }}
```
