---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: baseURL-相対 URL を作成する。
draft: false
hugoversion: null
keywords:
- urls
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- absURL
signature:
- relURL INPUT
title: relURL
workson: []
---

`absURL` と `relURL` はどちらも、サイトの [`config` ファイル][configuration] で設定された `baseURL` の値を考慮します。 `baseURL` が `https://example.com/hugo/` に設定されていると、以下のようになります。

```go-html-template
{{ "mystyle.css" | absURL }} → "https://example.com/hugo/mystyle.css"
{{ "mystyle.css" | relURL }} → "/hugo/mystyle.css"
{{ "http://gohugo.io/" | relURL }} →  "http://gohugo.io/"
{{ "http://gohugo.io/" | absURL }} →  "http://gohugo.io/"
```

最後の 2 つの例は奇妙に見えるかもしれませんが、非常に便利なものです。 たとえば、以下は、[SEO 用の JSON-LD 構造化データ][jsonld] において、コンテンツの一部の画像がローカルにホストされているかどうかに関わらず、`absURL` を使用する方法を示しています。

{{< code file="layouts/partials/schemaorg-metadata.html" download="schemaorg-metadata.html" >}}
<script type="application/ld+json">
{
    "@context" : "https://schema.org",
    "@type" : "BlogPosting",
    "image" : {{ apply .Params.images "absURL" "." }}
}
</script>
{{< /code >}}

上記は [apply 関数][apply function] を使用しており、Go テンプレート パーサーが `<script>` タグ内のオブジェクトを JSON エンコードする方法も公開しています。 そのようなタグ内の文字列をエスケープしないように Hugo に指示する方法の例については、[safeJS テンプレート関数][safejs] を参照してください。

{{% note "Ending Slash" %}}
`absURL` と `relURL` はスラッシュの欠落をスマートに処理しますが、URL に終了スラッシュがない場合は、URL に終了スラッシュを *追加しません*。
{{% /note %}}

[apply function]: /functions/apply/
[configuration]: /getting-started/configuration/
[jsonld]: https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data
[safejs]: /functions/safejs
