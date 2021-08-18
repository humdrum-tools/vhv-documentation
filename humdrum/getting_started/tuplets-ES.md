---
title: tutorial de codificación de grupos irregulares
lang: en es
ref: humdrum-getting_started-tuplets
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial tuplets
creation_date: 20 Aug 2017
translation_date: 18 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar grupos irregulares en datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/tuplets-ES.html
---

<!--{% include humdrum/tuplets.txt %}-->

## Grupos irregulares ##

Los grupos irregulares no difieren de los valores rítmicos normales, ya que describen cuántas notas de esa duración se suman para crear una duración de redonda.  Las corcheas de los tresillos se representan con el número "12" porque doce de ellas equivalen a la duración de una redonda. Las semicorcheas de un quintillo se representan con el número "20" porque 20 de ellas equivalen a la duración de una redonda.

{% include verovio.html
	humdrum-min-height="400px"
	evenNoteSpacing="1"
	source="tuplet1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tuplet1">
**kern
*M2/4
4g
20a
20b
20.a
40g
20a
=
12.f
24g
12a
4g
=
6b
6a
6g
=
2e
==
!!!filter: autobeam
</script>


### Representación ampliada del ritmo ###

Las duraciones de las notas que no dividen la duración de una redonda en un número entero de piezas iguales (cuando también se tienen en cuenta los puntillos), deben ser codificadas en una representación extendida de `**recip`.  Este sistema es entendido por VHV y [Humdrum Extras](http://extras.humdrum.org), pero no en el clásico Humdrum Toolkit (ver [rscale](http://extras.humdrum.org/man/rscale) para usar ritmos extendidos con el Humdrum Toolkit).

Algunos ejemplos de ritmos extendidos son las redondas de tresillo.  3/2 de una redonda de tresillo llenan la duración de una redonda normal, por lo que se representa con la cadena `3%2`.  Otra forma de conceptualizar esto es invertir los números en la cadena rítmica, observando que una redonda de tresillo es 2/3 de una nota entera:

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="ext1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="ext1">
**kern
*M2/1
=1
3%2d
3%2e
3%2f
=2
3%2.g
3f
3%2d
=3
1%2e
==
*-
</script>

Fíjate en el ritmo `1%2` del último compás.  Esto representa una cuadrada, ya que 1/2 de la cuadrada equivale a una redonda.  El `0` es un código especial que equivale al `1%2`, el `00` equivale al `1%4` (una longa) y el `000` equivale al `1%8` (una máxima).  Probablemente sea mejor utilizar el sistema de ceros para breves, máximas y longas, reservando los ritmos extendidos para la legibilidad y utilizar descripciones basadas en `%` casos rítmicos más complicados.

