---
title: filtro melisma
lang: en es
ref: filters-melisma
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 15 Sep 2019
translation_date: 8 Aug 2021
last_updated: 15 Sep 2019
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/melisma/index-ES.html
---

El filtro de melisma puede utilizarse para analizar la relación entre notas y sílabas en la música.

El comportamiento por defecto del filtro es resaltar las notas de todas las sílabas que tienen dos o más notas:

{% include verovio.html
	source="basic"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basic">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma
</script>


### Establecer un número mínimo de notas ##
La opción `-m` puede utilizarse para establecer el número mínimo de notas que se marcarán como melisma.  El valor por defecto es de 2 notas, este puede ser aumentado.  Aquí hay un ejemplo que establece el mínimo a 3, haciendo que las dos primeras palabras ya no se marquen como melismas:

{% include verovio.html
	source="three"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="three">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -m 3
</script>


### Mostrar los recuentos de melismas ###
La opción `-r` se puede utilizar para sustituir la letra por el recuento de notas de cada sílaba:

{% include verovio.html
	source="replace"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="replace">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -r
</script>

Vuelve a ejecutar el filtro de melisma para resaltar las notas de melisma:

{% include verovio.html
	source="rerun"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="rerun">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -r
!!!filter: melisma -m 3
</script>


### Opciones de la línea de comandos ###

La opción `-a` calculará la relación media nota-sílaba para las sílabas de melisma identificadas.

La opción `-p` calculará las relaciones nota-sílaba por parte.

La opción `-w` listará las palabras de la música que contengan un melisma.




