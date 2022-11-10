---
aliases:
- /pages
categories:
- variables and params
date: "2019-10-20"
description: Pages is the core page collection in Hugo and has many useful methods.
draft: true
keywords:
- pages
linktitle: null
menu:
  docs:
    parent: variables
    title: methods defined on a page collection
    weight: 21
sections_weight: 20
title: Pages Methods
toc: true
weight: 21
---

Also see [List templates](/templates/lists) for an overview of sort methods.

## .Next PAGE

`.Next` and `.Prev` on `Pages` work similar to the methods with the same names on `.Page`, but are more flexible (and slightly slower) as they can be used on any page collection.

`.Next` points **up** to the next page relative to the page sent in as the argument. Example: `{{with .Site.RegularPages.Next . }}{{.RelPermalink}}{{end}}`. Calling `.Next` with the first page in the collection returns `nil`.

## .Prev PAGE

`.Prev` points **down** to the previous page relative to the page sent in as the argument. Example: `{{with .Site.RegularPages.Prev . }}{{.RelPermalink}}{{end}}`. Calling `.Prev` with the last page in the collection returns `nil`.
