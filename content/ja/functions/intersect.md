---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns the common elements of two arrays or slices, in the same order
  as the first array.
draft: true
hugoversion: null
keywords:
- collections
- intersect
- union
- complement
- symdiff
lastmod: "2017-02-01"
linktitle: intersect
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- intersect SET1 SET2
title: intersect
workson: []
---
A useful example is to use it as `AND` filters when combined with where:

## AND filter in where query

```
{{ $pages := where .Site.RegularPages "Type" "not in" (slice "page" "about") }}
{{ $pages := $pages | union (where .Site.RegularPages "Params.pinned" true) }}
{{ $pages := $pages | intersect (where .Site.RegularPages "Params.images" "!=" nil) }}
```

The above fetches regular pages not of `page` or `about` type unless they are pinned. And finally, we exclude all pages with no `images` set in Page params.

See [union](/functions/union) for `OR`.


[partials]: /templates/partials/
[single]: /templates/single-page-templates/
