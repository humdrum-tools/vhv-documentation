---
title: Tutorial de codificación de grupos de barrado
lang: en es
ref: humdrum-getting_started-beaming
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial beaming
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Tutorial de cómo codificar grupos de barrado en **kern
sidebar: main_sidebar
permalink: /humdrum/getting_started/beaming-ES.html
---

<!--{% include humdrum/beaming.txt %}-->

## Beaming ##

Los barrados funcionan de forma similar a las ligaduras de prolongación.  El carácter "L" indica el inicio de un barrado, y el carácter "J" indica el final de un barrado.

{% include verovio.html
	humdrum-min-height="490px"
	evenNoteSpacing="1"
	source="beam1"
	scale="55"
	pageWidth="475"
%}
<script type="application/x-humdrum" id="beam1">
**kern
*M3/4
=1
8c
8d
8e
8f
8g
8a
=2
8cL
8dJ
8eL
8fJ
8gL
8aJ
=3
*M6/8
8cL
8d
8eJ
8fL
8g
8aJ
==
*-
</script>

Prueba a añadir barrados con agrupaciones irregulares en el primer compás del ejemplo.

### Barrado perezoso ###

VHV utiliza un sistema de barrado perezoso para unir las notas.  En lugar de especificar el principio/final de cada parte del barrado o su dirección, se indica el principio/final de un grupo de notas con los caracteres `L` y `J` (*es decir, codifica sólo el barrado primario):

Codificación de una descripción completa de los barrados:

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam2"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam2">
**kern
*M2/4
16.eLL
32fk
16.e
32fJJk
8fL
16gL
16aJJ
==
*-
</script>

que equivale a esta codificación de barrado *perezoso* de sólo el barrado principal (el más alejado de las cabezas de nota):

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam3"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam3">
**kern
*M2/4
16.eL
32f
16.e
32fJ
8fL
16g
16aJ
==
*-
</script>


{% include note.html
	content="Actualmente no se pueden dibujar barrados a través de las líneas de compás.  Si los inicios y finales de los compases no están equilibrados entre sí dentro de un compás, ninguna de las notas del compás se barrará, como se muestra en el siguiente ejemplo (intenta fijar los barrados en ese compás)."
%}

{% include verovio.html
	humdrum-min-height="425px"
	evenNoteSpacing="1"
	source="beam4"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam4">
**kern
*M4/4
=1
8cL
8f
8a
8eJ
8fL
8g
8f
8aJ
=2
8cL
8f
8a
8e
8fL
8g
8f
8aJ
==
*-
</script>


### Filtro autobeam ###

El [filtro autobeam](/filter/autobeam) puede utilizarse para unir las notas automáticamente, basándose en el compás predominante:

{% include verovio.html
	humdrum-min-height="365px"
	evenNoteSpacing="1"
	source="beam5"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam5">
**kern
*M3/4
8c
8d
8e
8f
8g
8a
=
*M6/8
8c
8d
8e
8f
8g
8a
==
*-
!!!filter: autobeam
</script>

Intenta copiar y pegar el contenido anterior en [VHV](http://verovio.humdrum.org), y luego presiona <span class="keystroke">alt-c</span> para compilar el filtro.  Esto ejecutará los datos de Humdrum a través del filtro y luego mostrará los resultados de vuelta en el editor de texto.  De lo contrario, los datos se filtran antes de ser convertidos en notación.


   