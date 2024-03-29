---
title: filtro extract
lang: en es
page_language: es
translator: David Rizo
translation_date: 8 Aug 2021
translation_update:
ref: filters-extract
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/extract/index-ES.html
---
El filtro extract puede utilizarse para manipular el orden de las columnas (*spines*), así como para eliminar columnas o añadir columnas en blanco.

He aquí un ejemplo de extracción de las partes exteriores de un coral a 4 voces:


{% include verovio.html
	source="chorale"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="chorale">
!!!filter: extract -s 1,4
**kern	**kern	**kern	**kern
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M3/4	*M3/4	*M3/4	*M3/4
4F	4A	4c	4f
=1	=1	=1	=1
4D	2A	2d	2f
4C	.	.	.
4BB-	4B-	4d	4f
=2	=2	=2	=2
4AA	2c	2e	2a
8BB-L	.	.	.
8AA	.	.	.
8GG	4B-	4e	4b-
8AAJ	.	.	.
=3	=3	=3	=3
8FFL	2A	2.f	2cc
8F	.	.	.
8E-	.	.	.
8D	.	.	.
8C	4B-	.	4dd
8BB-J	.	.	.
=4	=4	=4	=4
2.F;	2.A;	2.f;	2.cc;
=5	=5	=5	=5
4D	2A	4f	2f
4C	.	4e	.
4BB-	4B-	4d	4f
=6	=6	=6	=6
4F	4A	2c	2a
4E	4G	.	.
4D	4F	4d	4b-
=7	=7	=7	=7
4E	4G	4c	2cc
4C	4c	4e	.
4GG	4B	4g	4dd
=8	=8	=8	=8
2.C;	2.G;	2.e;	2.cc;
=9	=9	=9	=9
2F	2A	2f	2cc
[4B-	4B-	4f	4dd
=10	=10	=10	=10
4B-]	4c	4e	2cc
4A	4d	4f	.
[4G	4e	4g	4b-
=11	=11	=11	=11
4G]	4A	4c#	4.a
4F	4B	4d	.
.	.	.	8b-
4E	4c#	4e	8aL
.	.	.	8gJ
=12	=12	=12	=12
2D;	2d;	2A;	2f;
4AA	4cnX	4f	4f
=13	=13	=13	=13
4BB-	4d	4f	2g
4GG	4B-	8eL	.
.	.	8dJ	.
4C	4c	4e	4g
=14	=14	=14	=14
8FFL	2c	2f	2a
8GG	.	.	.
8AA	.	.	.
8BB-	.	.	.
8C	4c	4e	4g
8BB-J	.	.	.
=15	=15	=15	=15
4AA	4c	4.f	2f
4FF	4A	.	.
.	.	8gL	.
4CC	4c	8f	4g
.	.	8eJ	.
=16	=16	=16	=16
2.FF;	2.c;	2.f;	2.a;
=17	=17	=17	=17
4F	2A	2f	2cc
4E	.	.	.
4D	4B-	4f	4dd
=18	=18	=18	=18
4E	2G	4g	2cc
4D	.	4f	.
4C	4e	4g	4b-
=19	=19	=19	=19
8FL	4e	4g	4.a
8GJ	.	.	.
4A	4d	4f	.
.	.	.	8b-L
4AA	4c#	4e	8a
.	.	.	8gJ
=20	=20	=20	=20
2D;	2A;	2d;	2f;
4AA	4cnX	[4f	4f
=21	=21	=21	=21
4BB-	4d	4f]	2g
4GG	4B-	8eL	.
.	.	8dJ	.
4C	4c	4e	4g
=22	=22	=22	=22
8FFL	2c	2f	2a
8GG	.	.	.
8AA	.	.	.
8BB-	.	.	.
8C	4c	[4e	4g
8AAJ	.	.	.
=23	=23	=23	=23
4D	2A	4e]	2f
4C	.	4A	.
4BB-	4B-	4d	4g
=24	=24	=24	=24
2.AA;	2.E;	2.c#;	2.a;
=25	=25	=25	=25
4BB-	8r	2d	2d
.	8FL	.	.
4AA	8G	.	.
.	8A	.	.
4GG	8B-	[4d	4d
.	8AJ	.	.
=26	=26	=26	=26
4C	4G	4d]	2e
4BB-	8AL	8cL	.
.	8B-	8dJ	.
4AA	8c	[4e	4e
.	8B-J	.	.
=27	=27	=27	=27
8DL	4.A	4e]	8fL
8C	.	.	8e
8D	.	2d	8f
8E	8G	.	8g
8F	4F	.	8a
8DJ	.	.	8b-J
=28	=28	=28	=28
2.E;	2.G;	2.c;	2.cc;
=29	=29	=29	=29
4FF	4A	4c	2a
4GG	4B-	8fL	.
.	.	8eJ	.
4AA	4c	4f	4a
=30	=30	=30	=30
4BB-	4d	2f	2g
4GG	4B-	.	.
4C	[4c	4e	4g
=31	=31	=31	=31
4AA	4c]	8fL	[2.f
.	.	8e-	.
2BB-	8B-L	8d	.
.	8A	8c	.
.	8B-	8d	.
.	8GJ	8B-J	.
=32	=32	=32	=32
2.FF;	2.A;	2.c;	2.f;]
==	==	==	==
*-	*-	*-	*-
</script>

El filtro extract es idéntico a la herramienta de línea de comandos Humdrum Extras [extractx](http://extras.humdrum.org/man/extractx).  Consulta su documentación para ver más ejemplos de cómo utilizar el filtro extract.



