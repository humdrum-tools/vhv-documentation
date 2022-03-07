---
title: tutorial de codificación del ritmo
lang: en es
ref: humdrum-getting_started-rhythm
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial rhythm
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar el ritmo en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/rhythm-ES.html
---

<!--{% include humdrum/rhythm.txt %}-->

## Ritmo ##

Los ritmos `**kern` se dan en términos del número de unidades en que la duración de la nota dividirá una redonda.  Las redondas son `1`, ya que cabe justo una redonda en una redonda.  Las blancas son `2` ya que hay dos en una redonda.  Las negras son `4`, ya que hay cuatro en una redonda, etc.

Una excepción al sistema numérico para los ritmos se utiliza para algunas notas más largas que una redonda: las breves se representan con `0`, las longas con `00` y las máximas con `000`.

{% include verovio.html
	humdrum-min-height="300px"
	evenNoteSpacing="1"
	spacingLinear="1"
	source="rhy1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="rhy1">
**kern
000b
00b
0b
1b
2b
4b
8b
16b
32b
64b
128b
256b
==
*-
</script>

El valor de nota más corto que puede mostrar Verovio es una semigarrapatea, aunque se pueden representar valores más cortos en datos `**kern`.


### Puntillos ###

Los puntillos se representan con caracteres de punto (`.`).  El primero añade la mitad de la duración de la nota simple, el siguiente añade 1/4 adicional de la nota original, y así sucesivamente.

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="dots1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dots1">
**kern
4.b
4..b
4...b
4....b
4.....b
=-
4.......b
4........b
4.........b
4..........b
4...........b
==
*-
</script>

