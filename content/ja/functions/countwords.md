---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Counts the number of words in a string.
draft: true
hugoversion: null
keywords:
- counting
- word count
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- countrunes
signature:
- countwords INPUT
title: countwords
workson: []
---

The template function works similar to the [.WordCount page variable][pagevars].

```
{{ "Hugo is a static site generator." | countwords }}
<!-- outputs a content length of 6 words.  -->
```


[pagevars]: /variables/page/
