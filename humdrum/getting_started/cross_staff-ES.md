---
title: Tutorial de codificación de notas que cruzan pentagramas
lang: en es
ref: humdrum-getting_started-cross_staff
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial cross staff
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Tutorial de cómo codificar notas que cruzan pentagramas en **kern
sidebar: main_sidebar
permalink: /humdrum/getting_started/cross_staff-ES.html
---

<!--{% include humdrum/cross_staff.txt %}-->

## Notas que cruzan pentagramas ##

Las notas pueden almacenarse en la columna `**kern` de un pentagrama, pero aparecer en otro pentagrama aplicando un marcador RDF de orientación inmediatamente después de la altura de una nota.

{% include verovio.html
	humdrum-min-height="360px"
	source="cross1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="cross1">
**kern	**kern
*clefF4	*clefG2
*M4/4	*M4/4
=1	=1
1CC	16e
.	16d
.	16c
.	16B<
.	16G<
.	16F<
.	16E<
.	16D<
.	16C<
.	16BB<
.	16C<
.	16E<
.	16G<
.	16c<
.	16e
.	16g
=2	=2
16C	2cc/
16D	.
16E	.
16F	.
16G	.
16A	.
16B	.
16c>	.
16d>	2dd/
16e>	.
16f>	.
16g>	.
4f>\	.
=	=
*-	*-
!!!filter: autobeam
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


