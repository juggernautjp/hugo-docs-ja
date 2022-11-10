---
aliases: []
categories:
- functions
date: "2017-02-01"
deprecated: false
description: Returns a random permutation of a given array or slice.
draft: true
hugoversion: null
keywords:
- ordering
lastmod: "2017-04-30"
menu:
  docs:
    parent: functions
publishdate: "2017-02-01"
relatedfuncs:
- seq
signature:
- shuffle COLLECTION
title: shuffle
workson: []
---

{{< code file="shuffle-input.html" >}}
<!-- Shuffled sequence = -->
<div>{{ shuffle (seq 1 5) }}</div>
<!-- Shuffled slice =  -->
<div>{{ shuffle (slice "foo" "bar" "buzz") }}</div>
{{< /code >}}

This example would return the following:

{{< output file="shuffle-output.html" >}}
<!-- Shuffled sequence =  -->
<div>2 5 3 1 4</div>
<!-- Shuffled slice =  -->
<div>buzz foo bar</div>
{{< /output >}}

This example also makes use of the [slice](/functions/slice/) and [seq](/functions/seq/) functions.
