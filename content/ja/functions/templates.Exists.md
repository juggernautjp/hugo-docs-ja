---
aliases: []
categories:
- functions
date: "2018-11-01"
deprecated: false
description: Checks whether a template file exists under the given path relative to
  the `layouts` directory.
draft: true
hugoversion: "0.46"
keywords:
- templates
- template
- layouts
lastmod: "2018-11-01"
linktitle: ""
menu:
  docs:
    parent: functions
ns: ""
publishdate: "2018-11-01"
relatedfuncs: []
signature:
- templates.Exists PATH
tags: []
title: templates.Exists
toc: false
workson: []
---

A template file is any file living below the `layouts` directories of either the project or any of its theme components including partials and shortcodes.

The function is particularly handy with dynamic path. The following example ensures the build will not break on a `.Type` missing its dedicated `header` partial.

```go-html-template
{{ $partialPath := printf "headers/%s.html" .Type }}
{{ if templates.Exists ( printf "partials/%s" $partialPath ) }}
  {{ partial $partialPath . }}
{{ else }}
  {{ partial "headers/default.html" . }}
{{ end }}

```
