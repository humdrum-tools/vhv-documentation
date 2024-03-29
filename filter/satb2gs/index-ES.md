---
title: filtro satb2gs
lang: en es
page_language: es
translator: David Rizo
translation_date: 8 Aug 2021
translation_update:
ref: filters-satb2gs
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/satb2gs/index-ES.html
---
El filtro satb2gs se puede utilizar para convertir la disposición SATB de las partes en una disposición de un gran pentagrama.

Este es un ejemplo de procesamiento de un coral a cuatro voces:

{% include verovio.html
	source="chorale"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="chorale">
!!!filter: satb2gs
**kern	**kern	**kern	**kern
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]
*M4/4	*M4/4	*M4/4	*M4/4
4A	4c#	4e	4a
=1	=1	=1	=1
4G#	4B	4.e	4e
4F#	4A	.	4f#
.	.	8d#	.
8EL	4B	4e	4g#
8DnXJ	.	.	.
4C#	4c#	8eL	4a
.	.	8f#J	.
=2	=2	=2	=2
4BB	4d	8g#L	4b
.	.	8f#J	.
4EE#	4c#	4g#	8cc#L
.	.	.	8bJ
4FF#;	4c#;	4f#;	4a;
4F#	4f#	4a	8cc#L
.	.	.	8ddJ
=3	=3	=3	=3
8G#L	4e	8bL	4ee
8F#J	.	8aJ	.
4E	4B	8g#L	8eeL
.	.	8f#J	8ddJ
4A	4B	4e	8cc#L
.	.	.	8ddJ
4C#	4A	4e	4ee
=4	=4	=4	=4
4BB	4A	4f#	2dd
4E	4G#	4e	.
4AA;	4A;	4e;	4cc#;
4AA	4A	4e	4cc#
=5	=5	=5	=5
4BB	8AL	4b	4dd
.	8G#J	.	.
8C#L	4A	4e	4cc#
8DJ	.	.	.
4E	8G#L	8eL	4b
.	8g#J	8dJ	.
8F#L	8f#L	8c#L	8aL
8G#J	8eJ	8BJ	8bJ
=6	=6	=6	=6
4A	4e	8AL	4cc#
.	.	8aJ	.
4AA	4e	16gLL	4cc#
.	.	16f#J	.
.	.	8gJ	.
4D;	4d;	4f#;	4a;
8AL	4e	4a	8cc#L
8BJ	.	.	8ddJ
=7	=7	=7	=7
4c#	4e	8g#XL	4ee
.	.	8aJ	.
4G#	4e	4b	4ee
4A	8eL	8aL	8cc#L
.	8dJ	8bJ	8ddJ
4A#	8c#L	4cc#	4ee
.	8f#J	.	.
=8	=8	=8	=8
4B	4.f#	8cc#L	2dd
.	.	16bL	.
.	.	16a#JJ	.
4BB	.	4b	.
.	8e#	.	.
4F#;	4f#;	4a#;	4cc#;
4E#X	8c#L	4g#	4cc#
.	8BJ	.	.
=9	=9	=9	=9
8F#L	8AnXL	4.f#	4dd
8G#J	8BJ	.	.
4A	4c#	.	4cc#
.	.	8enX	.
8DL	8F#L	4d	4b
8EnXJ	8G#J	.	.
[4F#	4A	4c#	8anXL
.	.	.	8bJ
=10	=10	=10	=10
8F#L]	4G#	4c#	4cc#
16E#L	.	.	.
16D#JJ	.	.	.
8E#L	4G#	4c#	4cc#
8C#J	.	.	.
4F#;	4F#;	4c#;	4a;
4E	4G#	4e	4b
=11	=11	=11	=11
8AL	4A	4e	4cc#
8G#J	.	.	.
8F#L	4A	4f#	4cc#
8EJ	.	.	.
8D#L	4.B	8f#L	4f#
8BBJ	.	8d#J	.
8EL	.	[4e	4g#
8D#J	8B	.	.
=12	=12	=12	=12
8C#L	16ALL	4e]	8aL
.	16BJJ	.	.
8AAJ	4c#	.	8g#J
4BB	.	4d#	4f#
.	16BLL	.	.
.	16AJJ	.	.
4E;	4G#;	4B;	4e;
4C#	4G#	4c#	4e
=13	=13	=13	=13
4F#	8F#	8c#	4a
.	4f#	4dnX	.
4G#	.	.	4b
.	16eLL	8e	.
.	16dJJ	.	.
4.A	8c#L	8eL	4cc#
.	16BL	8f#J	.
.	16c#JJ	.	.
.	8dL	8g#L	8bL
8G	8eJ	8aJ	8cc#J
=14	=14	=14	=14
4F#	8A	[2a	4dd
.	4f#	.	.
8EL	.	.	4cc#
8DJ	8f#	.	.
2E	8BL	4a]	2b
.	16c#L	.	.
.	16dJJ	.	.
.	8eL	4g#	.
.	8dJ	.	.
=15	=15	=15	=15
2.AA;	2.c#;	2.e;	2.a;
==	==	==	==
*-	*-	*-	*-
</script>

El filtro satb2gs es idéntico a la herramienta de línea de comandos Humdrum Extras [satb2gs](http://extras.humdrum.org/man/satb2gs).  Consulta su documentación para ver más ejemplos de cómo utilizar el filtro satb2gs.



