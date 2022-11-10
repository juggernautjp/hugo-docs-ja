---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Runs the provided string through the Markdown processor.
draft: true
hugoversion: null
keywords:
- markdown
- content
lastmod: "2017-02-01"
linktitle: markdownify
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- markdownify INPUT
title: markdownify
workson: []
---


```
{{ .Title | markdownify }}
```

{{< new-in "0.93.0" >}} **Note**: `markdownify` now supports [Render Hooks][] just like [.RenderString](/functions/renderstring/).

[Render Hooks]: /templates/render-hooks/
