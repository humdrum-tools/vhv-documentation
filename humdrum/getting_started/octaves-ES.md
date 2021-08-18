---
title: tutorial de codificación de octavas
lang: en es
ref: humdrum-getting_started-octaves
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial octaves
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar las octavas en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/octaves-ES.html
---

<!--{% include humdrum/octaves.txt %}-->

## Octavas ##

La posición de la octava de una nota se indica en los datos del `**kern` como varias repeticiones del nombre de la nota en forma de letra mayúscula o minúscula. La octava del Do central se indica con una sola letra minúscula, y cada octava sucesivamente más alta repite una letra minúscula adicional para indicar la octava:

{% include verovio.html
	source="octave1"
	scale="55"
	pageWidth="1400"
	humdrum-min-height="120px"
%}
<script type="application/x-humdrum" id="octave1">
**kern
*clefG2
2c
2cc
2ccc
*-
</script>

Las octavas inferiores se indican con repeticiones sucesivas de letras mayúsculas:

{% include verovio.html
	source="octave2"
	scale="55"
	pageWidth="1400"
	humdrum-min-height="120px"
%}
<script type="application/x-humdrum" id="octave2">
**kern
*clefF4
2C
2CC
2CCC
*-
</script>

