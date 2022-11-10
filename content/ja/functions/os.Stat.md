---
aliases: []
categories:
- functions
date: "2018-08-07"
deprecated: false
description: Returns a FileInfo structure describing a file or directory.
draft: true
hugoversion: null
keywords:
- files
lastmod: "2021-11-26"
menu:
  docs:
    parent: functions
publishdate: "2018-08-07"
relatedfuncs:
- os.FileExists
- os.ReadDir
- os.ReadFile
signature:
- os.Stat PATH
title: os.Stat
workson: []
---
The `os.Stat` function attempts to resolve the path relative to the root of your project directory. If a matching file or directory is not found, it will attempt to resolve the path relative to the [`contentDir`]({{< relref "getting-started/configuration#contentdir">}}). A leading path separator (`/`) is optional.

```go-html-template
{{ $f := os.Stat "README.md" }}
{{ $f.IsDir }}    --> false (bool)
{{ $f.ModTime }}  --> 2021-11-25 10:06:49.315429236 -0800 PST (time.Time)
{{ $f.Name }}     --> README.md (string)
{{ $f.Size }}     --> 241 (int64)

{{ $d := os.Stat "content" }}
{{ $d.IsDir }}    --> true (bool)
```

Details of the `FileInfo` structure are available in the [Go documentation](https://pkg.go.dev/io/fs#FileInfo).
