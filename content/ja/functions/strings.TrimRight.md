---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a slice of a given string with all trailing characters contained
  in the cutset removed.
draft: true
hugoversion: null
keywords:
- strings
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- strings.TrimRight
signature:
- strings.TrimRight CUTSET STRING
title: strings.TrimRight
workson: []
---

Given the string `"abba"`, trailing `"a"`'s can be removed a follows:

    {{ strings.TrimRight "a" "abba" }} → "abb"

Numbers can be handled as well:

    {{ strings.TrimRight 12 1221341221 }} → "122134"
