---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a given string s without the provided trailing suffix string.
  If s doesn't end with suffix, s is returned unchanged.
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
- strings.TrimPrefix
signature:
- strings.TrimSuffix SUFFIX STRING
title: strings.TrimSuffix
workson: []
---

Given the string `"aabbaa"`, the specified suffix is only removed if `"aabbaa"` ends with it:

    {{ strings.TrimSuffix "a" "aabbaa" }} → "aabba"
    {{ strings.TrimSuffix "aa" "aabbaa" }} → "aabb"
    {{ strings.TrimSuffix "aaa" "aabbaa" }} → "aabbaa"
