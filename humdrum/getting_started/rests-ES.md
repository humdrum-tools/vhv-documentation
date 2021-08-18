---
title: Tutorial de codificación de silencios
lang: en es
ref: humdrum-getting_started-rests
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial rests
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar los silencios en **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/rests-ES.html
---

<!--{% include humdrum/rests.txt %}-->

## Silencios ##

Los silencios se representan con el carácter `r` en los datos de `**kern`. Los silencios de compás completo se codifican con su duración real, y si la duración del silencio coincide con la del compás, entonces el silencio se mostrará como un silencio de compás completo centrado, independientemente de su duración real (o como un silencio de compás de breve si la duración del compás es breve o mayor).

{% include verovio.html
	humdrum-min-height="275px"
	source="rest1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="rest1">
**kern
*clefG2
*M5/4
=1
4r
2.r
32r
8r
16r
32r
=2
4%5r
=3
*M2/1
0r
==
*-
</script>

