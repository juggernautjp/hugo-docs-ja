---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: 設定された baseURL に基づいて、絶対 URL を作成します。
draft: false
hugoversion: null
keywords:
- urls
lastmod: "2017-02-01"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- relURL
signature:
- absURL INPUT
title: absURL
workson: []
---

`absURL` と `relURL` の両方とも、サイトの [`config` ファイル][configuration] で設定された `baseURL` の値を考慮します。 `baseURL` に `https://example.com/hugo/` が設定されている場合は、以下のようになります。

```go-html-template
{{ "mystyle.css" | absURL }} → "https://example.com/hugo/mystyle.css"
{{ "mystyle.css" | relURL }} → "/hugo/mystyle.css"
{{ "http://gohugo.io/" | relURL }} →  "http://gohugo.io/"
{{ "http://gohugo.io/" | absURL }} →  "http://gohugo.io/"
```

最後の 2 つの例は奇妙に見えるかもしれませんが、非常に便利です。 たとえば、以下の例では、[JSON-LD 構造化データ (SEO)][jsonld] で `absURL` を使用する方法を示しています。 ここでは、コンテンツの一部の画像がローカルでホストされている場合とされていない場合があります。

{{< code file="layouts/partials/schemaorg-metadata.html" download="schemaorg-metadata.html" >}}
<script type="application/ld+json">
{
    "@context" : "http://schema.org",
    "@type" : "BlogPosting",
    "image" : {{ apply .Params.images "absURL" "." }}
}
</script>
{{< /code >}}

上記は [apply 関数][apply function] を使用しており、Go テンプレート パーサーが `<script>` タグ内のオブジェクトを JSON エンコードする方法も公開しています。 このようなタグ内の文字列をエスケープしないように Hugo に指示する方法の例については、[safeJS テンプレート関数][safejs] を参照してください。

{{% note "Ending Slash" %}}
`absURL` と `relURL` はスラッシュの欠落をスマートに処理しますが、URL に終了スラッシュがない場合は、終了スラッシュを *追加しません*。
{{% /note %}}

[apply function]: /functions/apply/
[configuration]: /getting-started/configuration/
[jsonld]: https://developers.google.com/search/docs/guides/intro-structured-data
[safejs]: /functions/safejs
