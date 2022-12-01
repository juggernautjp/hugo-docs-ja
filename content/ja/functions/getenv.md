---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 環境変数の値を返します。環境変数が設定されていない場合は、空文字列を返します。
draft: false
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
例:

```go-html-template
{{ os.Getenv "HOME" }} --> /home/victor
{{ os.Getenv "USER" }} --> victor
```

以下のようにすると、サイトをビルドする際に値を渡すことができます。

```bash
MY_VAR1=foo MY_VAR2=bar hugo

# または

export MY_VAR1=foo
export MY_VAR2=bar
hugo
```

次に、テンプレート内の値を取得します。

```go-html-template
{{ os.Getenv "MY_VAR1" }} --> foo
{{ os.Getenv "MY_VAR2" }} --> bar
```
