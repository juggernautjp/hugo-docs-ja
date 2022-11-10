---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a slice of a given string with all leading characters contained
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
- strings.TrimLeft CUTSET STRING
title: strings.TrimLeft
workson: []
---

Given the string `"abba"`, leading `"a"`'s can be removed a follows:

    {{ strings.TrimLeft "a" "abba" }} → "bba"

Numbers can be handled as well:

    {{ strings.TrimLeft 12 1221341221 }} → "341221"
