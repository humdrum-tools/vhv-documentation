---
title: tutorial de codificación de acordes
lang: en es
ref: humdrum-getting_started-chords
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial chord
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar los acordes en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/chords-ES.html
---

<!--{% include humdrum/chords.txt %}-->

## Acordes ##

Los acordes se crean añadiendo varias notas a un token, separadas por un solo carácter de espacio.  Deben duplicarse los ritmos y las articulaciones de cada nota, pero no las ligaduras de expresión, los calderones o los barrados.

{% include verovio.html
	source="chord1"
	scale="55"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="chord1">
**kern
*clefG2
4c 4e 4g
4e' 4g' 4cc'
4g^ 4cc^ 4ee^
1c 1e 1g 1cc;
*-
</script>

