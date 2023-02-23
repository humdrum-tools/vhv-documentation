---
title: filtro myank
lang: en es
page_language: es
translator: David Rizo
translation_date: 8 Aug 2021
translation_update:
ref: filters-myank
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/myank/index-ES.html
---

El filtro myank puede utilizarse para extraer compases de una partitura completa.

He aquí un ejemplo de extracción de los compases 5 al final de la pieza en un coral de Bach.

{% include verovio.html
	source="chorale042"
	scale="50"
	pageWidth="1250"
	tabsize="10"
%}

<script type="application/x-humdrum" id="chorale042">
!!!filter: myank -m 5-$
**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]
*M4/4	*M4/4	*M4/4	*M4/4
4A	4e	4a	4cc#
=1	=1	=1	=1
8dL	4d	4f#	4a
8c#J	.	.	.
4B	4d	4g#	4b
4A	4e	4a	4cc#
4G#	4e	4b	4ee
=2	=2	=2	=2
4F#	4f#	4a	4dd
4G#	4e	4b	4dd
4A;	4e;	4a;	4cc#;
4C#	4e	4a	4ee
=3	=3	=3	=3
8F#L	4f#	4a	4dd
8G#J	.	.	.
4A	4e	4a	4cc#
4D	4f#	4a	4b
4E	4e	4g#	4b
=4	=4	=4	=4
2.AA;	2.e;	2.a;	2.cc#;
8EL	4e	4g#	4b
8F#J	.	.	.
=5	=5	=5	=5
4G#	4B	4e	4b
4E	4e	4g#	4b
4A	4e	4a	4cc#
4E	8eL	4g#	4b
.	8dJ	.	.
=6	=6	=6	=6
4F#	4c#	4f#	4a
4BB	4d	4g#	4b
4C#;	4c#;	4e#;	4g#;
4C#	4c#	4e#	4g#
=7	=7	=7	=7
4F#	4c#	4f#	4a
4E	4enX	4g#	4b
4A	2e	4a	4cc#
4G#	.	4e	8bL
.	.	.	8cc#J
=8	=8	=8	=8
4F#	4d	4a	4dd
4E	4e	4a	4cc#
4D	4f#	4a	2b
4E	8eL	4g#	.
.	8dJ	.	.
=9	=9	=9	=9
2.AA;	2.c#;	2.e;	2.a;
==	==	==	==
*-	*-	*-	*-
</script>

El filtro myank es idéntico a la herramienta de línea de comandos Humdrum Extras [myank](http://extras.humdrum.org/man/myank). Consulta su documentación para ver más ejemplos de cómo utilizar el filtro myank.



