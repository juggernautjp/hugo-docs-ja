---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Adds the relative URL with correct language prefix according to site
  configuration for multilingual.
draft: true
hugoversion: null
keywords:
- multilingual
- i18n
- urls
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- relLangURL INPUT
title: relLangURL
workson: []
---

`absLangURL` and `relLangURL` functions are similar to their [`absURL`](/functions/absurl/) and [`relURL`](/functions/relurl/) relatives but will add the correct language prefix when the site is configured with more than one language. (See [Configure Languages][multiliconfig].)

So for a site  `baseURL` set to `https://example.com/hugo/` and the current language is `en`:

```
{{ "blog/" | absLangURL }} → "https://example.com/hugo/en/blog/"
{{ "blog/" | relLangURL }} → "/hugo/en/blog/"
```

[multiliconfig]: /content-management/multilingual/#configure-languages
