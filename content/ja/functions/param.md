---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Calls page or site variables into your template.
draft: true
hugoversion: null
keywords:
- front matter
lastmod: "2017-04-30"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- default
signature:
- .Param KEY
title: .Param
toc: null
workson: []
---

In Hugo, you can declare [site-wide params][sitevars] (i.e. in your [configuration][]), as well as params for [individual pages][pagevars].

A common use case is to have a general value for the site and a more specific value for some of the pages (e.g., an image).

You can use the `.Param` method to call these values into your template. The following will first look for an `image` param in a specific content's [front matter][]. If not found, Hugo will look for an `image` param in your site's configuration:

```
$.Param "image"
```

{{% note %}}
The `Param` method may not consider empty strings in a content's front matter as "not found." If you are setting preconfigured front matter fields to empty strings using Hugo's archetypes, it may be best to use the [`default` function](/functions/default/) instead of `Param`. See the [related issue on GitHub](https://github.com/gohugoio/hugo/issues/3366).
{{% /note %}}


[configuration]: /getting-started/configuration/
[front matter]: /content-management/front-matter/
[pagevars]: /variables/page/
[sitevars]: /variables/site/
