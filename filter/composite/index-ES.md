---
title: filtro composite
lang: en es
page_language: es
translator: David Rizo
translation_date: 8 Aug 2021
translation_update:
ref: filters-composite
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/composite/index-es.html
---
El filtro `composite` puede utilizarse para extraer el ritmo compuesto de una partitura de varias voces o de varios instrumentos.


Este es un ejemplo de partitura con dos instrumentos:

{% include verovio.html
	source="twoparts"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="twoparts">
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>
Cada instrumento tiene un ritmo diferente.  El filtro `composite` colapsa los ataques de nota de cada parte en un único patrón rítmico.

{% include verovio.html
	source="composite"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="composite">
!!!filter: composite
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Colocación del ritmo compuesto por debajo del sistema ###
Utiliza la opción `- p` para colocar el pentagrama rítmico compuesto debajo del sistema musical existente:


{% include verovio.html
	source="prepend"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="prepend">
!!!filter: composite -p
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Colocación del ritmo compuesto por encima del sistema ###

Utiliza la opción `-a` para colocar el pentagrama rítmico compuesto sobre el sistema existente:


{% include verovio.html
	source="append"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="append">
!!!filter: composite -a
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Barrado de grupos de notas ### 

Por defecto, los ritmos del ritmo compuesto no serán barrados:

{% include verovio.html
	source="nobeam"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="nobeam">
!!!filter: composite -p
**kern	**kern
*M4/4	*M4/4
4c	2c
16dL	.
8d	.
16dJ	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>

Añade la opción `-b` para agrupar las notas según el compás:

{% include verovio.html
	source="beam"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="beam">
!!!filter: composite -pb
**kern	**kern
*M4/4	*M4/4
4c	2c
16dL	.
8d	.
16dJ	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


### Adornos ### 
Los adornos se incluyen en el análisis del ritmo compuesto:

{% include verovio.html
	source="grace"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="grace">
!!!filter: composite -pb
**kern	**kern
*M4/4	*M4/4
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>

pero los adornos pueden eliminarse del análisis del ritmo compuesto con la opción `-G`:


{% include verovio.html
	source="nograce"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="nograce">
!!!filter: composite -pbG
**kern	**kern
*M4/4	*M4/4
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


### Tono de las notas rítmicas compuestas ###
La opción `--pitch` puede establecer el tono de la nota compuesta.

{% include verovio.html
	source="pitch"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="325px"
	humdrum-min-width="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="pitch">
!!!filter: composite -pbG --pitch f#
**kern	**kern
*k[f#]	*k[f#]
*M4/4	*M4/4
=1	=1
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf#	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>

