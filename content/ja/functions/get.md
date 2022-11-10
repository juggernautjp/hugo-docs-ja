---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Accesses positional and ordered parameters in shortcode declaration.
draft: true
hugoversion: null
keywords:
- shortcodes
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
needsexample: true
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- .Get INDEX
- .Get KEY
title: .Get
workson: []
---


`.Get` is specifically used when creating your own [shortcode template][sc], to access the [positional and named](/templates/shortcode-templates/#positional-vs-named-parameters) parameters passed to it. When used with a numeric INDEX, it queries positional parameters (starting with 0). With a string KEY, it queries named parameters.

When accessing a named parameter that does not exist, `.Get` returns an empty string instead of interrupting the build. The same goes with positional parameters in hugo version 0.40 and after. This allows you to chain `.Get` with `if`, `with`, `default` or `cond` to check for parameter existence. For example, you may now use:

```
{{ $quality := default "100" (.Get 1) }}
```

[sc]: /templates/shortcode-templates/
