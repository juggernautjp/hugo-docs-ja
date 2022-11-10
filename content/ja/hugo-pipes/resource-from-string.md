---
categories:
- asset management
date: "2018-07-14"
description: Hugo Pipes allows the creation of a resource from a string.
draft: true
keywords: []
linkTitle: Resource from String
menu:
  docs:
    parent: pipes
    weight: 90
publishdate: "2018-07-14"
sections_weight: 90
title: Creating a resource from a string
weight: 90
---

It is possible to create a resource directly from the template using `resources.FromString` which takes two arguments, the given string and the resource target path.

The following example creates a resource file containing localized variables for every project's languages.

```go-html-template
{{ $string := (printf "var rootURL = '%s'; var apiURL = '%s';" (absURL "/") (.Param "API_URL")) }}
{{ $targetPath := "js/vars.js" }}
{{ $vars := $string | resources.FromString $targetPath }}
{{ $global := resources.Get "js/global.js" | resources.Minify }}

<script src="{{ $vars.Permalink }}"></script>
<script src="{{ $global.Permalink }}"></script>
```
