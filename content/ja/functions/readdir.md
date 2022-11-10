---
aliases: []
categories:
- functions
deprecated: false
description: Returns an array of FileInfo structures sorted by filename, one element
  for each directory entry.
draft: true
hugoversion: null
keywords:
- files
lastmod: "2021-11-26"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- os.FileExists
- os.ReadFile
- os.Stat
signature:
- os.ReadDir PATH
- readDir PATH
title: readDir
workson: []
---
The `os.ReadDir` function resolves the path relative to the root of your project directory. A leading path separator (`/`) is optional.

With this directory structure:

```text
content/
├── about.md
├── contact.md
└── news/
    ├── article-1.md
    └── article-2.md
```

This template code:

```go-html-template
{{ range os.ReadDir "content" }}
  {{ .Name }} --> {{ .IsDir }}
{{ end }}
```

Produces:

```html
about.md --> false
contact.md --> false
news --> true
```

Note that `os.ReadDir` is not recursive.

Details of the `FileInfo` structure are available in the [Go documentation](https://pkg.go.dev/io/fs#FileInfo).

For more information on using `readDir` and `readFile` in your templates, see [Local File Templates]({{< relref "/templates/files" >}}).
