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
needsexample: true
publishdate: "2017-02-01"
relatedfuncs:
- HasMenuCurrent
signature:
- PAGE.IsMenuCurrent MENU MENUENTRY
title: .IsMenuCurrent
workson:
- menus
---

`.IsMenuCurrent` is a method in `Page` object returning a _boolean_ value. It
returns `true` if the PAGE is the same object as the `.Page` in MENUENTRY in a
given MENU.

You can find its example use in [menu templates](/templates/menu-templates/).
