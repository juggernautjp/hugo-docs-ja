---
categories:
- functions
date: "2021-10-08"
description: Replaces path separators with slashes (`/`) and removes extraneous separators.
draft: true
keywords:
- path
- clean
menu:
  docs:
    parent: functions
relatedfuncs:
- path.Base
- path.BaseName
- path.Dir
- path.Ext
- path.Join
- path.Split
signature:
- path.Clean PATH
title: path.Clean
---

`path.Clean` replaces path separators with slashes (`/`) and removes extraneous separators, including trailing separators.

```
{{ path.Clean "foo//bar" }} → "foo/bar"
{{ path.Clean "/foo/bar/" }} → "/foo/bar"
```

On a Windows system, if `.File.Path` is `foo\bar.md`, then:

```
{{ path.Clean .File.Path }} → "foo/bar.md"
```
