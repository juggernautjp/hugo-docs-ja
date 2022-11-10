---
aliases: []
categories:
- functions
date: "2019-08-13"
deprecated: false
description: Determine whether a given string ends with the provided trailing suffix
  string.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2019-08-13"
menu:
  docs:
    parent: functions
publishdate: "2019-08-13"
relatedfuncs:
- hasPrefix
signature:
- strings.HasSuffix STRING SUFFIX
title: strings.HasSuffix
workson: []
---

    {{ $pdfPath := "/path/to/some.pdf" }}
    {{ strings.HasSuffix $pdfPath "pdf" }} → true
    {{ strings.HasSuffix $pdfPath "txt" }} → false
