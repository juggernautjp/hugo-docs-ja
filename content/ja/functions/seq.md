---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Creates a sequence of integers.
draft: true
hugoversion: null
keywords: []
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- seq LAST
- seq FIRST LAST
- seq FIRST INCREMENT LAST
title: seq
workson: []
---

It's named and used in the model of [GNU's seq][].

```
3 → 1, 2, 3
1 2 4 → 1, 3
-3 → -1, -2, -3
1 4 → 1, 2, 3, 4
1 -2 → 1, 0, -1, -2
```

## Example: `seq` with `range` and `after`

You can use `seq` in combination with `range` and `after`. The following will return 19 elements:

```
{{ range after 1 (seq 20)}}
{{ end }}
```

However, when ranging with an index, the following may be less confusing in that `$indexStartingAt1` and `$num` will return `1,2,3 ... 20`:

```
{{ range $index, $num := (seq 20) }}
$indexStartingAt1 := (add $index 1)
{{ end }}
```


[GNU's seq]: https://www.gnu.org/software/coreutils/manual/html_node/seq-invocation.html#seq-invocation
