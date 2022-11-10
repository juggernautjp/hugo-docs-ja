---
categories:
- asset management
date: "2018-07-14"
description: Hugo Pipes can bundle any number of assets together.
draft: true
keywords: []
lastmod: "2018-07-14"
menu:
  docs:
    parent: pipes
    weight: 60
publishdate: "2018-07-14"
sections_weight: 60
title: Asset bundling
weight: 60
---

Asset files of the same MIME type can be bundled into one resource using `resources.Concat` which takes two arguments, a target path and a slice of resource objects.

```go-html-template
{{ $plugins := resources.Get "js/plugins.js" }}
{{ $global := resources.Get "js/global.js" }}
{{ $js := slice $plugins $global | resources.Concat "js/bundle.js" }}
```
