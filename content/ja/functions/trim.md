---
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a slice of a passed string with all leading and trailing characters
  from cutset removed.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- trim INPUT CUTSET
title: trim
workson: []
---

```
{{ trim "++Batman--" "+-" }} → "Batman"
```

`trim` *requires* the second argument, which tells the function specifically what to remove from the first argument. There is no default value for the second argument, so **the following usage will not work**:

```
{{ trim .Inner}}
```

Instead, the following example tells `trim` to remove extra new lines from the content contained in the [shortcode `.Inner` variable][shortcodevars]:

```
{{ trim .Inner "\n" }}
```

{{% note %}}
Go templates also provide a simple [method for trimming whitespace](/templates/introduction/#whitespace) from either side of a Go tag by including a hyphen (`-`).
{{% /note %}}


[shortcodevars]: /variables/shortcodes/
