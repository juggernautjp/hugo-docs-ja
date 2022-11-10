---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a slice of strings by splitting STRING by DELIM.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2022-11-06"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- split STRING DELIM
title: split
workson: []
---

Examples:

```go-html-template
{{ split "tag1,tag2,tag3" "," }} → ["tag1", "tag2", "tag3"]
{{ split "abc" "" }} → ["a", "b", "c"]
```


{{% note %}}
`split` essentially does the opposite of [delimit]({{< ref "functions/delimit" >}}). While `split` creates a slice from a string, `delimit` creates a string from a slice.
{{% /note %}}
