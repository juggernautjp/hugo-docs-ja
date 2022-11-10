---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a given string s without the provided leading prefix string.
  If s doesn't start with prefix, s is returned unchanged.
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
- strings.TrimSuffix
signature:
- strings.TrimPrefix PREFIX STRING
title: strings.TrimPrefix
workson: []
---

Given the string `"aabbaa"`, the specified prefix is only removed if `"aabbaa"` starts with it:

    {{ strings.TrimPrefix "a" "aabbaa" }} → "abbaa"
    {{ strings.TrimPrefix "aa" "aabbaa" }} → "bbaa"
    {{ strings.TrimPrefix "aaa" "aabbaa" }} → "aabbaa"
