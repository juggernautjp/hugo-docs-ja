---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns the value of an environment variable, or an empty string if the
  environment variable is not set.
draft: true
hugoversion: null
keywords: []
lastmod: "2021-11-26"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs: []
signature:
- os.Getenv VARIABLE
- getenv VARIABLE
title: getenv
workson: []
---
Examples:

```go-html-template
{{ os.Getenv "HOME" }} --> /home/victor
{{ os.Getenv "USER" }} --> victor
```

You can pass values when building your site:

```bash
MY_VAR1=foo MY_VAR2=bar hugo

OR

export MY_VAR1=foo
export MY_VAR2=bar
hugo
```

And then retrieve the values within a template:

```go-html-template
{{ os.Getenv "MY_VAR1" }} --> foo
{{ os.Getenv "MY_VAR2" }} --> bar
```
