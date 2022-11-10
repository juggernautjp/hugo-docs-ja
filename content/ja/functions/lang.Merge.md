---
aliases: []
categories:
- functions
comments: null
date: "2018-03-16"
deprecated: false
description: Merge missing translations from other languages.
draft: true
hugoversion: null
keywords:
- multilingual
menu:
  docs:
    parent: functions
relatedfuncs: []
signature:
- lang.Merge FROM TO
title: lang.Merge
toc: false
workson: []
---

As an example:

```bash
{{ $pages := .Site.RegularPages | lang.Merge $frSite.RegularPages | lang.Merge $enSite.RegularPages }}
```

Will "fill in the gaps" in the current site with, from left to right, content from the French site, and lastly the English.


A more practical example is to fill in the missing translations from the other languages:

```bash
{{ $pages := .Site.RegularPages }}
{{ range .Site.Home.Translations }}
{{ $pages = $pages | lang.Merge .Site.RegularPages }}
{{ end }}
 ```
