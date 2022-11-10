---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: null
draft: true
hugoversion: null
keywords:
- menus
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- IsMenuCurrent
signature:
- PAGE.HasMenuCurrent MENU MENUENTRY
title: .HasMenuCurrent
toc: false
workson:
- menus
---

`.HasMenuCurrent` is a method in `Page` object returning a _boolean_ value. It
returns `true` if the PAGE is the same object as the `.Page` in one of the
**children menu entries** under MENUENTRY in a given MENU.

{{< new-in "0.86.0" >}} If MENUENTRY's `.Page` is a [section](/content-management/sections/) then, from Hugo `0.86.0`, this method also returns true for any descendant of that section..

You can find its example use in [menu templates](/templates/menu-templates/).
