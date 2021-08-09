---
title: humdiff filter
lang: en es
ref: filters-humdiff
author: Craig Stuart Sapp
translator: 
creation_date: 15 Sep 2019
translation_date: 
last_updated: 15 Sep 2019
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/humdiff/index-ES.html
---

El filtro humdiff identifica y marca automáticamente las diferencias entre dos o más partituras de la misma música que tengan la misma duración. El filtro es útil para la validación de datos cuando se codifican partituras utilizando <a target="_blank" href="https://en.wikipedia.org/wiki/Two_pass_verification">método de doble entrada de datos</a>, así como para la preparación de <a target="_blank" href="https://chaucer.fas.harvard.edu/types-editions#criticaledition">ediciones críticas</a>.

Aquí hay dos ejemplos de partituras con algunas diferencias:

{% include verovio.html
	source="score1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-height="200px"
%}
<script type="text/x-humdrum" id="score1">
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
</script>


{% include verovio.html
	source="score2"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-height="200px"
%}
<script type="text/x-humdrum" id="score2">
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>

El filtro humdiff identifica las diferencias entre las dos partituras y resaltará las notas de la primera partitura que sean diferentes a las de la segunda:

{% include verovio.html
	source="humdiff1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiff1">
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>

Observa que el filtro humdiff requiere dos (o más) segmentos de datos, y el comando de filtrado debe comenzar con cuatro `!!!!`, indicando que el filtro se aplica a múltiples segmentos de datos.

## Partitura de referencia ## 
Por defecto, el filtro humdiff utilizará el primer segmento de datos como la partitura de referencia con la que se compararán todos los demás segmentos de datos.  La partitura de referencia se mostrará con notas resaltadas que muestran dónde otras partituras tienen notas diferentes.

La opción `-r` selecciona una partitura diferente en el flujo de datos de Humdrum para usarla como referencia cuando no aparece primero.  Aquí hay un ejemplo de las mismas dos partituras que se comparan, pero ahora la segunda partitura en el flujo de datos se utiliza como la partitura de referencia:

{% include verovio.html
	source="humdiffr2"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffr2">
!!!!filter: humdiff -r 2
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>
Observa que las notas negras de la partitura gráfica resultante coinciden entre las dos versiones de la música.  Las notas resaltadas son diferentes y se muestran las de la edición de referencia.

Un método alternativo para seleccionar la partitura de referencia es utilizar el filtro [chooser](/filter/chooser).  Este filtro reordena el orden de los segmentos de datos dentro de un flujo de datos de Humdrum:

{% include verovio.html
	source="humdiffchooser"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchooser">
!!!!filter: chooser -s 2,1
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>


## Comparaciones de partituras múltiples ##
El filtro humdiff puede comparar varias notas con una nota de referencia, siempre que todas las notas tengan la misma duración.  Cualquier nota en la partitura de referencia que difiera de la partitura de comparación será resaltada.  He aquí un ejemplo de tres partituras, cada una de las cuales tiene una diferencia con la partitura de referencia.  La primera partitura es una escala de Do mayor, la segunda añade un sostenido en el Fa, y la tercera añade un bemol en el La. Esto hace que se resalten el Fa y el La en la partitura original:

{% include verovio.html
	source="humdiffmultiple"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-width="250px"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffmultiple">
!!!!filter: humdiff
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f#
=2
4g
4a
4b
4cc
==
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a-
4b
4cc
==
*-
</script>
Prueba a cambiar la partitura de referencia en el ejemplo anterior, por ejemplo, añadiendo `-r 2` a la línea de filtro en el texto anterior.

## Color de resalte ##
La opción `-c` se puede utilizar para establecer el color de resaltado.  El color puede ser cualquier nombre de color SVG/HTML o color hexadecimal.

{% include verovio.html
	source="humdiffcolor"
	scale="60"
	pageWidth="800"
	tabsize="16"
	humdrum-min-height="225px"
	humdrum-min-width="300px"
%}
<script type="text/x-humdrum" id="humdiffcolor">
!!!!filter: humdiff -c limegreen
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4g
4f
=
*-
</script>

Prueba a poner el color en `hotpink` y `#ff8800`.


## Ejemplo con una mazurca de Chopin ##
He aquí un ejemplo que compara los dos últimos compases de la mazurca de Chopin en si menor, op 30/2, entre dos primeras ediciones diferentes:

<ol>
<li> Breitkopf &amp; H&auml;rtel</li>
<li> Maurice Schlesinger</li>
</ol>

En la primera comparación, la partitura B&amp;H es la referencia, con notas rojas que indican las diferencias con la edición de Schlesinger:

{% include verovio.html
	source="humdiffchopin"
	scale="60"
	pageWidth="900"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchopin">
!!!!filter: humdiff
!!!!SEGMENT: breitkopf
!!!OPS: 30
!!!OMN: 2
!!!PPR: Breitkopf & Härtel
!!!PPP: Leipzig
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e# 4c#	.	4ccc# 4cc#	.
4b 4e# 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[[
*clefF4	*	*	*
=64	=64	=64	=64
*ped	*	*	*
4FF#	2ff#)	4r	.
4f# 4c# 4F#	.	4cc# 4a	.
*Xped	*	*	*
4r	4ryy	4r	.
==	==	==	==
*-	*-	*-	*-
!!!!SEGMENT: schlesinger
!!!OPS: 30
!!!ONM: 2
!!!PPR: M. Schlesinger
!!!PPP: Paris
**kern	**kern	**dynam
*part1	*part1	*part1
*staff2	*staff1	*
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
*b:	*b:	*
*M3/4	*M3/4	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e 4c#	.	4ccc# 4cc#	.
4b 4e 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[
*	*v	*v	*
*clefF4	*	*
=64	=64	=64
4f# 4c# 4F#	4ff# 4a)	.
4F# 4FF#	4fff# 4ff#	fz
4r	4r	.
!!LO:TX:a:B:rj:t=FINE
==	==	==
*-	*-	*-
</script>
Y en la siguiente comparación, la edición de Schlesinger es la referencia, siendo las notas verdes diferentes a las de la edición B&amp;H:

{% include verovio.html
	source="humdiffchopin2"
	scale="60"
	pageWidth="900"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchopin2">
!!!!filter: chooser -s 2,1
!!!!filter: humdiff -c limegreen
!!!!SEGMENT: breitkopf
!!!OPS: 30
!!!OMN: 2
!!!PPR: Breitkopf & Härtel
!!!PPP: Leipzig
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e# 4c#	.	4ccc# 4cc#	.
4b 4e# 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[[
*clefF4	*	*	*
=64	=64	=64	=64
*ped	*	*	*
4FF#	2ff#)	4r	.
4f# 4c# 4F#	.	4cc# 4a	.
*Xped	*	*	*
4r	4ryy	4r	.
==	==	==	==
*-	*-	*-	*-
!!!!SEGMENT: schlesinger
!!!OPS: 30
!!!ONM: 2
!!!PPR: M. Schlesinger
!!!PPP: Paris
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e 4c#	.	4ccc# 4cc#	.
4b 4e 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[
*	*v	*v	*
*clefF4	*	*
=64	=64	=64
4f# 4c# 4F#	4ff# 4a)	.
4F# 4FF#	4fff# 4ff#	fz
4r	4r	.
==	==	==
*-	*-	*-
</script>



