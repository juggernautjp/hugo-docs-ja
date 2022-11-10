---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Converts all characters in the provided string to title case.
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
- title INPUT
title: title
workson: []
---


```
{{title "BatMan"}}` → "Batman"
```

Can be combined in pipes. In the following snippet, the link text is cleaned up using `humanize` to remove dashes and `title` to convert the value of `$name` to Initial Caps.

```
{{ range $name, $items := .Site.Taxonomies.categories }}
    <li><a href="{{ printf "%s/%s" "categories" ($name | urlize | lower) | absURL }}">{{ $name | humanize | title }} ({{ len $items }})</a></li>
{{ end }}
```

## Configure Title Case

The default is AP Stylebook, but you can [configure it](/getting-started/configuration/#configure-title-case).
