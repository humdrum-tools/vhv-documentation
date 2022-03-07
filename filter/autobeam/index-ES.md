---
title: autobeam filter
lang: en pl es
ref: filters-autobeam
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 23 Apr 2017
translation_date: 7 Aug 2021
last_updated: 23 Apr 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/autobeam/index-es.html
---

El filtro autobeam puede utilizarse para añadir automáticamente barras de agrupación a las notas
de acuerdo con el compás predominante.  Este es un ejemplo en el que el filtro 
filtro autobeam se está aplicando a la música, que contiene un
compás de música en 3/4 y otro en 6/8.

{% include verovio.html
	source="meterchange"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="meterchange">
!!!filter: autobeam
**kern
*M3/4
8c
8e
8d
8f
8g
8e
=
*M6/8
8c
8d
8e
8g
8f
8e
==
*-
</script>

Prueba a eliminar el filtro de los datos anteriores de Humdrum y vea qué ocurre.

En el editor VHV, también puedes escribir <span class="keypress">alt-c</span>
para "compilar" el filtro, lo que hará que los marcadores del barrado se 
se añaden a los datos en el editor.  (El comando <span class="keypress">alt-c</span>
no funcionará en esta página).


### Selección de una columna (spine) concreta ###

Si sólo hay que procesar un solo pentagrama, se utiliza la opción `-t` (pista). 
La primera pista (columna) es la que está más a la izquierda (al principio) de los datos.  Este es un
ejemplo de barrado de la segunda pista (columna) dejando la primera inalterada:


{% include verovio.html
	source="track"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="track">
!!!filter: autobeam -t 2
**kern	**kern
*M3/4	*M3/4
8c	8cc
8e	8ee
8d	8dd
8f	8ff
8g	8gg
8e	8ee
=	=
*M6/8	*M6/8
8c	8cc
8d	8dd
8e	8ee
8g	8gg
8f	8ff
8e	8ee
==	==
*-	*-
</script>


### Selección de un pentagrama concreto ###

Además de seleccionar por pista, también se puede seleccionar por pentagrama.
Específicamente por el número de columa del `**kern`, comenzando por el 1 como el más bajo
más bajo (columna "kern" de la izquierda en los datos).  En los siguientes datos
la última columna es la tercera pista, pero el segundo pentagrama:


{% include verovio.html
	source="kern"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="8"
%}
<script type="application/json" id="kern">
!!!filter: autobeam -k 2
**kern	**fing	**kern
*M3/4	*	*M3/4
8c	1	8cc
8e	3	8ee
8d	2	8dd
8f	4	8ff
8g	3	8gg
8e	5	8ee
=	=	=
*M6/8	*	*M6/8
8c	1	8cc
8d	2	8dd
8e	3	8ee
8g	5	8gg
8f	4	8ff
8e	3	8ee
==	==	==
*-	*-	*-
</script>


### Quitar barras de agrupación ###
Utiliza la opción "r" para eliminar las agrupaciones existentes.  Este es un ejemplo
en el que se eliminan los barrados del pentagrama superior:

{% include verovio.html
	source="remove"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="remove">
!!!filter: autobeam -r -k2
**kern	**kern
*M3/4	*M3/4
8cL	8ccL
8e	8ee
8d	8dd
8f	8ff
8g	8gg
8eJ	8eeJ
=	=
*M6/8	*M6/8
8cL	8ccL
8d	8dd
8e	8ee
8g	8gg
8f	8ff
8eJ	8eeJ
==	==
*-	*-
</script>


### División de barras de agrupación por letra ###
La opción `l` puede utilizarse para romper las barras de manera que las sílabas de la letra
comiencen al principio de los grupos de barras.  En el siguiente ejemplo, el pentagrama
ejemplo, el pentagrama superior muestra el barrado original, y el pentagrama inferior muestra el 
grupo después de ser procesado con el filtro `autobeam -l`.  Esto divide
el barrado del segundo tiempo en dos grupos: una sola corchea con "is" debajo,
y la sílaba "so-" que inicia un nuevo grupo de dos notas del resto
del tiempo.

{% include verovio.html
	source="lyrics"
	scale="60"
	humdrum-min-height="365px"
	spacingLinear="0.65"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="lyrics">
**kern	**text
*M4/4	*
=1	=1
8.cL	This_
16dJ	.
8fL	is
16dL	so-
16eJJ	.
4d	-me
4c	text.
==	==
*-	*-
!!!filter: extract -s 1-$,1-$
!!!filter: autobeam -l -k 1
</script>

Observa el filtro `extract -s 1-$,1-$` que duplica el sistema original
de la música. Entonces la opción `-k 1` para el autobeam aplica la rotura del barrado para los inicios de sílaba sólo a la primera columna de kern (el pentagrama inferior del sistema).


