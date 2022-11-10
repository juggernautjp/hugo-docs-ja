---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Removes any trailing newline characters.
draft: true
hugoversion: null
keywords:
- trim
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- truncate
signature:
- chomp INPUT
title: chomp
toc: true
workson: []
---

Useful in a pipeline to remove newlines added by other processing (e.g., [`markdownify`](/functions/markdownify/)).

```
{{chomp "<p>Blockhead</p>\n"}} → "<p>Blockhead</p>"
```
