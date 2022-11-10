---
categories:
- asset management
date: "2018-07-14"
description: Hugo Pipes allows the creation of a resource from an asset file using
  Go Template.
draft: true
keywords: []
linkTitle: Resource from Template
menu:
  docs:
    parent: pipes
    weight: 80
publishdate: "2018-07-14"
sections_weight: 80
title: Creating a resource from template
weight: 80
---

In order to use Hugo Pipes function on an asset file containing Go Template magic the function `resources.ExecuteAsTemplate` must be used.

The function takes three arguments: the resource target path, the template context, and the resource object.

```go-html-template
// assets/sass/template.scss
$backgroundColor: {{ .Param "backgroundColor" }};
$textColor: {{ .Param "textColor" }};
body{
  background-color:$backgroundColor;
  color: $textColor;
}
// [...]
```

```go-html-template
{{ $sassTemplate := resources.Get "sass/template.scss" }}
{{ $style := $sassTemplate | resources.ExecuteAsTemplate "main.scss" . | resources.ToCSS }}
```
