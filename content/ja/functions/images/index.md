---
aliases:
- /functions/imageconfig/
categories:
- functions
date: "2017-02-01"
description: images 名前空間は、フィルターおよびその他の画像関連関数のリストを提供します。
draft: false
keywords:
- images
menu:
  docs:
    parent: functions
title: 画像フィルター
toc: true
---

これらのフィルターを画像に適用する方法については、[images.Filter](#filter) を参照してください。

## Overlay

{{< new-in "0.80.0" >}}

{{% funcsig %}}
images.Overlay SRC X Y
{{% /funcsig %}}

Overlay は、元画像を x y の位置でオーバーレイするフィルタを作成します。たとえば、以下のとおりです。


```go-html-template
{{ $logoFilter := (images.Overlay $logo 50 50 ) }}
{{ $img := $img | images.Filter $logoFilter }}
```

フィルターを 1 回だけ適用する必要がある場合は、上記の短縮版の以下を使用します。

```go-html-template
{{ $img := $img.Filter (images.Overlay $logo 50 50 )}}
```

上記は、`$img` の左上隅 (`x=50, y=50` の位置) に `$logo` をオーバーレイ表示します。

## Text

{{< new-in "0.90.0" >}}

`Text` フィルターを使用すると、画像にテキストを追加できます。

{{% funcsig %}}
images.Text TEXT DICT)
{{% /funcsig %}}

以下の例では、指定した色、サイズ、位置の画像に、テキスト `Hugo rocks!` を追加します。

```go-html-template
{{ $img := resources.Get "/images/background.png"}}
{{ $img = $img.Filter (images.Text "Hugo rocks!" (dict
    "color" "#ffffff"
    "size" 60
    "linespacing" 2
    "x" 10
    "y" 20
))}}
```

必要に応じて、カスタムフォントをロードすることができます。 フォントを Hugo の `Resource` としてロードし、オプションとして設定します。

```go-html-template

{{ $font := resources.Get "https://github.com/google/fonts/raw/main/apache/roboto/static/Roboto-Black.ttf" }}
{{ $img := resources.Get "/images/background.png"}}
{{ $img = $img.Filter (images.Text "Hugo rocks!" (dict
    "font" $font
))}}
```


## Brightness

{{% funcsig %}}
images.Brightness PERCENTAGE
{{% /funcsig %}}

Brightness は、画像の明るさを変更するフィルターを作成します。
パーセント パラメーターは範囲内 (-100、100) である必要があります。

### ColorBalance

{{% funcsig %}}
images.ColorBalance PERCENTAGERED PERCENTAGEGREEN PERCENTAGEBLUE
{{% /funcsig %}}

ColorBalance は、画像のカラー バランスを変更するフィルターを作成します。
各カラー チャネル (赤、緑、青) のパーセント パラメーターは、範囲 (-100、500) である必要があります。

## Colorize

{{% funcsig %}}
images.Colorize HUE SATURATION PERCENTAGE
{{% /funcsig %}}

Colorize は、画像をカラー化するフィルターを作成します。
hue パラメーターはカラーホイール上の角度で、通常は (0, 360) の範囲です。
saturation パラメーターは、範囲 (0、100) でなければなりません。
パーセント パラメーターは効果の強さを指定し、範囲（0、100）である必要があります。

## Contrast

{{% funcsig %}}
images.Contrast PERCENTAGE
{{% /funcsig %}}

Contrast は、画像のコントラストを変更するフィルターを作成します。
パーセントパラメーターは、範囲 (-100、100) である必要があります。

## Gamma

{{% funcsig %}}
images.Gamma GAMMA
{{% /funcsig %}}

Gamma は、画像にガンマ補正を行うフィルターを作成します。
The gamma parameter must be positive. Gamma = 1 gives the original image.
Gamma less than 1 darkens the image and gamma greater than 1 lightens it.

## GaussianBlur

{{% funcsig %}}
images.GaussianBlur SIGMA
{{% /funcsig %}}

GaussianBlur creates a filter that applies a gaussian blur to an image.

## Grayscale

{{% funcsig %}}
images.Grayscale
{{% /funcsig %}}

Grayscale creates a filter that produces a grayscale version of an image.

## Hue

{{% funcsig %}}
images.Hue SHIFT
{{% /funcsig %}}

Hue creates a filter that rotates the hue of an image.
The hue angle shift is typically in range -180 to 180.

## Invert

{{% funcsig %}}
images.Invert
{{% /funcsig %}}

Invert creates a filter that negates the colors of an image.

## Pixelate

{{% funcsig %}}
images.Pixelate SIZE
{{% /funcsig %}}

Pixelate creates a filter that applies a pixelation effect to an image.

## Saturation

{{% funcsig %}}
images.Saturation PERCENTAGE
{{% /funcsig %}}

Saturation creates a filter that changes the saturation of an image.

## Sepia

{{% funcsig %}}
images.Sepia PERCENTAGE
{{% /funcsig %}}

Sepia creates a filter that produces a sepia-toned version of an image.

## Sigmoid

{{% funcsig %}}
images.Sigmoid MIDPOINT FACTOR
{{% /funcsig %}}

Sigmoid creates a filter that changes the contrast of an image using a sigmoidal function and returns the adjusted image.
It's a non-linear contrast change useful for photo adjustments as it preserves highlight and shadow detail.

## UnsharpMask

{{% funcsig %}}
images.UnsharpMask SIGMA AMOUNT THRESHOLD
{{% /funcsig %}}

UnsharpMask creates a filter that sharpens an image.
The sigma parameter is used in a gaussian function and affects the radius of effect.
Sigma must be positive. Sharpen radius roughly equals 3 * sigma.
The amount parameter controls how much darker and how much lighter the edge borders become. Typically between 0.5 and 1.5.
The threshold parameter controls the minimum brightness change that will be sharpened. Typically between 0 and 0.05.

## Other Functions

### Filter

{{% funcsig %}}
IMAGE | images.Filter FILTERS...
{{% /funcsig %}}

Can be used to apply a set of filters to an image:

```go-html-template
{{ $img := $img | images.Filter (images.GaussianBlur 6) (images.Pixelate 8) }}
```

Also see the [Filter Method](/content-management/image-processing/#filter).

### ImageConfig

Parses the image and returns the height, width, and color model.

The `imageConfig` function takes a single parameter, a file path (_string_) relative to the _project's root directory_, with or without a leading slash.

{{% funcsig %}}
images.ImageConfig PATH
{{% /funcsig %}}

```go-html-template
{{ with (imageConfig "favicon.ico") }}
favicon.ico: {{.Width}} x {{.Height}}
{{ end }}
```
