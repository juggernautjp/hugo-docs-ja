---
aliases: []
categories:
- functions
date: "2018-11-07"
description: '`collections.Complement` (alias `complement`) gives the elements of
  a collection that are not in any of the others.'
draft: true
hugoversion: "0.51"
keywords:
- collections
- intersect
- union
menu:
  docs:
    parent: functions
signature:
- COLLECTION | complement COLLECTION [COLLECTION]...
title: complement
---

Example:

```go-html-template
{{ $pages := site.RegularPages | first 50 }}
{{ $news := where $pages "Type" "news" | first 5 }}
{{ $blog := where $pages "Type" "blog" | first 5 }}
{{ $other := $pages | complement $news $blog | first 10 }}
```

The above is an imaginary use case for the home page where you want to display different page listings in sections/boxes on different places on the page: 5 from `news`, 5 from the `blog` and then 10 of the pages not shown in the other listings, to _complement_ them.
