---
title: Corchetes y llaves de sistemas
lang: en es
ref: system decoration instrument names
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum instrument names
creation_date: 24 Feb 2020
translation_date: 10 Aug 2021
last_updated: 24 Feb 2020
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de la decoración del sistema y los nombres de los pentagramas
sidebar: main_sidebar
permalink: /humdrum/system/index-ES.html
---

En esta página se describen los aspectos visuales de las partituras que incluyen llaves, corchetes, nombres de pentagramas y abreviaturas, así como nombres de grupos y abreviaturas.


## Nombres de pentagramas ##

Los nombres de los pentagramas se dan en interpretaciones tándem que comienzan con la cadena `*I"`.  Los nombres de pentagrama están relacionados con <a target="_blank">códigos de instrumento</a>, como `*Icello` para el violonchelo.  Los nombres de pentagrama son una descripción visual del instrumento u otro texto que se muestra al comienzo de un movimiento, mientras que los códigos de instrumento son para fines de análisis.  Dar un nombre de pentagrama anulará la visualización de un nombre generado automáticamente a partir de un código de instrumento al comienzo de los datos (pero la generación automática de nombres de pentagrama a partir del código de instrumento no está implementada todavía).

He aquí un ejemplo de partitura de cuarteto de cuerda, en la que se indican los nombres de cada pentagrama (pruebe a cambiar los nombres en el cuadro de texto de la izquierda, y se actualizarán a medida que escriba en el de la derecha):

{% include verovio.html
	source="quartet"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="quartet">
**kern	**kern	**kern	**kern
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
</script>



## Abreviaturas de nombre de pentagrama ##

Después del primer sistema de un movimiento, no se mostrarán los nombres de los instrumentos en los sistemas sucesivos.  Se puede dar una abreviatura de pentagrama opcional anteponiendo `*I'` a la cadena de abreviatura del pentagrama.

{% include verovio.html
	source="quartet2"
	humdrum-min-width="400"
	pageWidth="1250"
	spacingLinear="0.24"
	tabsize="12"
%}
<script type="application/json" id="quartet2">
**kern	**kern	**kern	**kern
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*I'vc.	*I'vla.	*I'vln. 2	*I'vln. 1
*M4/4	*M4/4	*M4/4	*M4/4
=1	=1	=1	=1
1CC	1c	1g	1ee
=2	=2	=2	=2
1DD	1D	1f	1aa
=3	=3	=3	=3
1EE	1G	1b	1gg
=4	=4	=4	=4
1FF	1F	1a	1cc
=5	=5	=5	=5
1GG	1D	1g	1b
=6	=6	=6	=6
1AA	1C	1e	1a
=7	=7	=7	=7
1BB	1D	1d	1f
=8	=8	=8	=8
1C;	1C;	1e;	1g;
==	==	==	==
*-	*-	*-	*-
</script>


## Estilos de sistemas ##

### Estilos por defectos ###

Cuando el sistema contiene sólo un pentagrama, no se añade ninguna decoración al sistema:

{% include verovio.html
	source="single"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="single">
**kern
*I"Cello
*I'vc.
*M4/4
=1
1CC
=2
1DD
=3
1EE
=
*-
</script>


Cuando el sistema contenga dos pentagramas, se añadirá automáticamente una llave, y los pentagramas se barrarán juntos (aunque esto no debe hacerse si hay letras unidas al pentagrama superior).

{% include verovio.html
	source="double"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="double">
**kern	**kern
*part1	*part1
*I"Piano	*I"Piano
*M4/4	*M4/4
=1	=1
1CC	1ee
=2	=2
1DD	1b
=3	=3
1EE	1g
=	=
*-	*-
</script>

Cuando haya tres o más pentagramas, se añadirá automáticamente un corchete, pero los pentagramas no se barrarán juntos.

{% include verovio.html
	source="triple"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="triple">
**kern	**kern	**kern
*I"part 3	*I"part 2	*I"part 1
*M4/4	*M4/4	*M4/4
=1	=1	=1
1CC	1ee	1gg
=2	=2	=2
1DD	1b	1ff
=3	=3	=3
1EE	1g	1ee
=	=	=
*-	*-	*-
</script>


## Decoración del sistema ##

Para anular los estilos de corchetes y barras por defecto, una línea que empiece por `!!!system-decoration:` puede dar un estilo diferente.  Para utilizar este sistema, se espera que todas las partes contengan enumeraciones de pentagramas, y que estos números de pentagramas estén referenciados en la cadena de decoración del sistema.


Este es un ejemplo para un cuarteto de cuerda, donde la decoración del sistema conecta los compases de todos los pentagramas:


{% include verovio.html
	source="barquart"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: [(s1,s2,s3,s4)]
</script>

### Comodín de pentagrama ###

Si sólo necesitas un único corchete o llave para todo el sistema, con o sin barras, puedes utilizar `*` para representar todos los pentagramas.

{% include verovio.html
	source="barquart2"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart2">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: [(*)]
</script>

Aquí está un ejemplo de la eliminación del soporte, pero manteniendo el barrado:

{% include verovio.html
	source="barquart3"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart3">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: (*)
</script>

Ten en cuenta que los paréntesis alrededor de los pentagramas (o el símbolo de comodín) harán que los pentagramas se barren juntos.

Aquí está un ejemplo de la eliminación del corchete, así como el barrado:

{% include verovio.html
	source="barquart4"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart4">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: *
</script>



## Nombre de un gran pentagrama ##

Hay varios métodos para dar una etiqueta al gran pentagrama. El primer método consiste en añadir marcadores `*part` en cada columna, seguidos de enteros que coincidan con el cero.

{% include verovio.html
	source="piano"
	humdrum-min-width="200"
	tabsize="12"
%}
<script type="application/json" id="piano">
**kern	**kern
*part1	*part1
*I"Piano	*
*M4/4	*M4/4
=	=
1CC	1f
=	=
*-	*-
</script>

Otro método es utilizar etiquetas de grupo, que empiezan por `*I""`, en lugar de etiquetas de parte, que empiezan por `*I"`.  Esto también tiene que estar coordinado con los marcadores `*group` que indican los pentagramas que deben agruparse:

{% include verovio.html
	source="piano2"
	humdrum-min-width="200"
	tabsize="12"
%}
<script type="application/json" id="piano2">
**kern	**kern
*group1	*group1
*I""Piano	*
*M4/4	*M4/4
=	=
1CC	1f
=	=
*-	*-
</script>


## Agrupación de clases de instrumentos ##

Las interpretaciones tándem de clases de instrumentos pueden utilizarse de forma equivalente a las interpretaciones de `*grupo#`.  He aquí un ejemplo:

{% include verovio.html
	source="ic"
	humdrum-min-width="500"
	humdrum-max-height="240"
	tabsize="12"
%}
<script type="application/json" id="ic">
**kern	**kern	**kern	**kern	**kern	**kern	**kern	**kern	**kern
*staff9	*staff8	*staff7	*staff6	*staff5	*staff4	*staff3	*staff2	*staff1
*ICstr	*ICstr	*ICstr	*ICstr	*ICbras	*ICbras	*ICww	*ICww	*ICww	
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1	*I"Trombone	*I"Trumpet	*I"Bassoon	*I"Oboe	*I"Flute
*IclefF4	*IclefC3	*IclefG2	*IclefG2	*IclefF4	*IclefG2	*IclefF4	*IclefG2	*IclefG2
*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=	=	=	=	=	=
1CC	1c	1cc	1ccc	1C	1cc	1C	1cc	1ccc
=	=	=	=	=	=	=	=	=
*-	*-	*-	*-	*-	*-	*-	*-	*-
!!!system-decoration: [(ww)][(bras)][(str)]
</script>

## Agrupación sin decoración ##

Este es un ejemplo de cómo no dar decoración a un grupo utilizando paréntesis angulares (`<>`) en la cadena de decoración del sistema:

{% include verovio.html
	source="nodeco"
	humdrum-min-width="500"
	humdrum-min-height="340"
	tabsize="12"
%}
<script type="application/json" id="nodeco">
**kern	**kern	**kern	**kern	**kern
*	*	*	*group1	*group1
*	*	*	*I""Tenori	*I""Tenori
*part4	*part4	*part3	*part2	*part1
*I"Organo	*I"Organo	*I"Basso	*	*
*I'Org	*I'Org	*I'B	*I'T	*I'T
*staff5	*staff4	*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefF4	*clefC4	*clefC4
*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M3/4	*M3/4	*M3/4	*M3/4	*M3/4
=1	=1	=1	=1	=1
2.FF	2.a 2.ff	4.F	4.A	4.f
.	.	8F	8A	8f
.	.	4F	4A	4f
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: &lt;g1&gt;,p3,{(p4)}
</script>




