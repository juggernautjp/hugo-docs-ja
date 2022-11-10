---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Declares the provided string as a known safe JavaScript string.
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
- safeJS INPUT
title: safeJS
workson: []
---

In this context, *safe* means the string encapsulates a known safe EcmaScript5 Expression (e.g., `(x + y * z())`).

Template authors are responsible for ensuring that typed expressions do not break the intended precedence and that there is no statement/expression ambiguity as when passing an expression like `{ foo:bar() }\n['foo']()`, which is both a valid expression and a valid program with a very different meaning.

Example: Given `hash = "619c16f"` defined in the front matter of your `.md` file:

* <span class="good">`<script>var form_{{ .Params.hash | safeJS }};…</script>` &rarr; `<script>var form_619c16f;…</script>`</span>
* <span class="bad">`<script>var form_{{ .Params.hash }};…</script>` &rarr; `<script>var form_"619c16f";…</script>`</span>
