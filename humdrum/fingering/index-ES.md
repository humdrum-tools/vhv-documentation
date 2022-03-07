---
title: Digitacióm
lang: en es
ref: humdrum-fingering
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum fingering
creation_date: 23 Mar 2018
translation_date: 10 Aug 2021
last_updated: 23 Mar 2018
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar las digitaciones en las columnas **fing
sidebar: main_sidebar
permalink: /humdrum/fingering/index-ES.html
---


Las digitaciones pueden ser codificadas en columnas Humdrum `**fing`:

{% include verovio.html
	source="fingering"
	humdrum-min-height="460px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}
<script type="application/json" id="fingering">
!!!OTL: C major scale
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4c	1
4d	2
4e	3
4f	1
=2	=2
4g	2
4a	3
4b	4
4cc	5
=3	=3
4b	4
4a	3
4g	2
4f	1
=4	=4
4e	3
4d	2
2c	1
==	==
*-	*-
</script>


Las digitaciones pueden colocarse en cualquier orden de columnas después de una columna `**kern` para el pentagrama en el que deben aparecer. He aquí un ejemplo de inclusión de datos de digitación y de dinámica para el mismo pentagrama utilizando la suite para violonchelo nº 1 de J.S. Bach en sol mayor, BWV 1007, Menuet II. 1 en sol mayor, BWV 1007, Menuet II.  Las columnas `**fing` y `**dynam` también pueden intercambiarse.

{% include verovio.html
	source="bwv1007"
	humdrum-min-height="460px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}

<script type="application/json" id="bwv1007">

!!!OTL: J.S. Bach
!!!OPR: Cello suite no. 1 in G major
!!!OTL: Menuet II
!!!SCA: BWV 1007
!!!ONB: mm 1-2
**kern	**fing	**dynam
*clefF4	*	*
*k[b-e-]	*	*
*M3/4	*	*
(8B-uL	2	p
8A	.	.
8B-)	.	.
(8D'	1	.
8E-'	2	.
8GG'J)	0	.
=2	=2	=2
4FF	1	.
(4A~	3	.
4D~)	0	.
=	=	=
*-	*-	*-

</script>


## Acordes ##

Las digitaciones de las notas de los acordes están separadas por espacios.


{% include verovio.html
	source="chord"
	humdrum-min-height="260px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}
<script type="application/json" id="chord">
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4c 4e	1 3
4d 4f	2 4
4e 4g	3 5
=2	=2
4c 4e 4g	1 3 5
4d 4f 4a	1 3 5
4e 4g 4b	1 3 5
==	==
*-	*-
</script>


Las digitaciones de los acordes deben ordenarse de tonos bajos a tonos altos para las notas de la mano derecha en la música de piano, mientras que las digitaciones de las notas de la mano izquierda deben ordenarse de tonos altos a tonos bajos. 

{% include verovio.html
	source="chord2"
	humdrum-min-height="180px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}
<script type="application/json" id="chord2">
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4c 4e 4g	1 3 5
4g 4e 4c	1 3 5
4e 4g 4c	1 3 5
==	==
*-	*-
</script>


{% include warning.html
	content="Left-hand fingering not yet implemented."
%}


## Colorear las digitaciones con CSS ##

Las digitaciones se marcan en la imagen SVG de salida de Verovio con la clase `fingering`. Esto permite que las digitaciones sean estilizadas en páginas web como ésta:

{% include verovio.html
	source="dmajor"
	humdrum-min-height="460px"
	tabsize="10"
	scale="55"
	pageWidth="860"
%}

<script type="application/json" id="dmajor">
!!!OTL: D major scale
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4d	1
4e	2
4f#	3
4g	1
=2	=2
4a	2
4b	3
4cc#	4
4dd	5
=3	=3
4cc#	4
4b	3
4a	2
4g	1
=4	=4
4f#	3
4e	2
2d	1
==	==
*-	*-
</script>


<style>

#dmajor-svg .fingering {
	fill: red;
}

</style>

Utilizando la definición de CSS:

```css
#dmajor-svg .fingering { fill: red; }
```



