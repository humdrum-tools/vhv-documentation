---
title: tutorial de codificación de alturas
lang: en es
ref: humdrum-getting_started-pitch
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial pitch
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar alturas de forma básica en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/pitch-ES.html
---

<!--{% include humdrum/pitch.txt %}-->

## Altura de notas ##

He aquí un breve ejemplo musical de notas, cada una de las cuales contiene un ritmo y luego una altura:

{% include verovio.html
	source="pitch1"
	scale="55"
	pageWidth="1400"
	humdrum-min-height="170px"
%}
<script type="application/x-humdrum" id="pitch1">
**kern
4c
4d
4e
4f
*-
</script>

`4` representa una negra, y `c`, `d`, `e` y `f` representan los cuatro primeros tonos de la cuarta octava (octava de Do central).  El ejemplo musical es interactivo y cambia cada vez que escribes texto en la casilla de la izquierda, así que prueba a añadir a la notación los tonos de Sol, La y Si en la misma octava, de esta manera:  

{% include verovio.html
	humdrum-visible="false"
	source="pitch2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch2">
**kern
4c
4d
4e
4f
4g
4a
4b
*-
</script>


Experimenta con los números para generar otros ritmos, como las blancas y las corcheas:

{% include verovio.html
	humdrum-visible="false"
	source="pitch3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch3">
**kern
8c
2d
8e
8f
4g
4a
2b
*-
</script>

Fíjate en el orden del ritmo y luego del tono en las notas codificadas.  El orden puede invertirse, aunque el orden canónico es primero el ritmo y luego la altura.  Prueba a invertir el orden de una nota como `4c` a `c4` y vea qué ocurre con la nota en la notación gráfica.
