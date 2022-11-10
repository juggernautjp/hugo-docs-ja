---
categories:
- functions
date: "2017-09-08"
description: Return one of two arguments, depending on the value of a third argument.
draft: true
hugoversion: 0.27
menu:
  docs:
    parent: functions
relatedfuncs:
- default
signature:
- cond CONTROL VAR1 VAR2
title: cond
toc: false
---

`cond` returns *VAR1* if *CONTROL* is true, or *VAR2* if it is not.

Example:

```
{{ cond (eq (len $geese) 1) "goose" "geese" }}
```

Would emit "goose" if the `$geese` array has exactly 1 item, or "geese" otherwise.

{{% warning %}}
Whenever you use a `cond` function, *both* variable expressions are *always* evaluated. This means that a usage like `cond false (div 1 0) 27` will throw an error because `div 1 0` will be evaluated *even though the condition is false*.

In other words, the `cond` function does *not* provide [short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation) and does *not* work like a normal [ternary operator](https://en.wikipedia.org/wiki/%3F:) that will pass over the first expression if the condition returns `false`.
{{% /warning %}}
