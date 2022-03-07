---
title: tutorial de codificación de pentagramas múltiples
lang: en es
ref: humdrum-getting_started-multiple_staves
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial multiple staves
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar múltiples pentagramas en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/multiple_staves-ES.html
---

<!--{% include humdrum/multiple_staves.txt %}-->

## Múltiples pentagramas ##

Cada columna `**kern` en los datos producirá un pentagrama en la notación gráfica.  El pentagrama más bajo es la columna más a la izquierda de los datos, y el más alto en la notación es la columna más a la derecha.

{% include verovio.html
	humdrum-min-height="320px"
	source="staves1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="staves1">
**kern	**kern
*M4/4	*M4/4
=1	=1
1C	4c
.	4e
.	4g
.	4cc
=2	=2
1GG	4dd
.	4b
.	4f
.	4a
=3	=3
1C;	1g;
==	==
*-	*-
</script>


He aquí un ejemplo más complicado en el que el número de voces cambia en cada pentagrama:

{% include verovio.html
	humdrum-min-height="450px"
	humdrum-min-width="350px"
	source="staves2"
	scale="45"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="staves2">
**kern	**kern
*M4/4	*M4/4
=1	=1
*	*^
1E	1cc	4a
.	.	4g
*	*	*^
.	.	4f/	2c\
.	.	4e/	.
*	*v	*v	*v
=2	=2
*^	*^
*	*	*	*^
1E	4r	4r	2gg	4d/
.	2EE	2.ccc	.	4g
.	.	.	2ryy	4f
.	8FFL	.	.	4e
.	8GGJ	.	.	.
*	*	*v	*v	*v
*v	*v	*
=2	=2
1AA;	1f;
==	==
*-	*-

</script>

Ten en cuenta que cuando las subcolumnas de los pentagramas adyacentes se fusionan al mismo tiempo (al final del compás 2), las fusiones deben escalonarse para mayor claridad de la agrupación.  Además, cuando una columna necesita expandirse de una a tres voces, debe haber dos expansiones `*^` (la primera para pasar de una a dos subcolumnas, y la segunda para pasar de dos a tres columnas).  Observa también el uso de `2ryy`, que se utiliza para retrasar la fusión de las subcolumnas hasta el final del compás (de lo contrario, las dos subcolumnas de la derecha podrían fusionarse antes de fusionarse con la primera subcolumna del pentagrama al final del compás).  Ten también en cuenta que las subcolumnas no deben terminar antes de la duración completa de la última nota de la subcolumna (así, las dos primeras subcolumnas del pentagrama superior del compás 2 no pueden fusionarse a mitad del compás, ya que la nota de la primera subcolumna aún no ha terminado de sonar).
