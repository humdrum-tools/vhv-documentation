---
title: tutorial de codificación de la letra de la música
lang: en es
ref: humdrum-getting_started-lyrics
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial lyrics
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar la letra de la música en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/lyrics-ES.html
---

<!--{% include humdrum/lyrics.txt %}-->

## Letra de la música ##

La letra se añaden a un pentagrama colocando una o más columnas `**text` después de una columna de `**kern`.

{% include verovio.html
	humdrum-min-height="350px"
	source="text1"
	scale="55"
	pageWidth="1100"
%}
<script type="application/x-humdrum" id="text1">
!!!OTL@@DE: Liebes-A-B-C
!!!COM: Pohlenz, August
!!!CDT: 1790/07/03/-1843/03/09/
!!!ODT: 1827
!!!OMD: Allegretto
!!!LYR: Gerhard, Wilhelm
!!!LDT: 1826
!!!OCL: Erk, Ludwig
!!!GCO: Deutscher Liederschatz, Band 1
**kern	**text	**text	**text	**text	**text	**text	**text
*clefG2	*	*	*	*	*	*	*
*k[b-]	*	*	*	*	*	*	*
*F:	*	*	*	*	*	*	*
*M3/8	*	*	*	*	*	*	*
=1	=1	=1	=1	=1	=1	=1	=1
8f	A	E	I	M	Q	U	Yp-
8e	B	F	K	N	R	V	-si-
8f	C	G	und	O	S	W	-lon
=2	=2	=2	=2	=2	=2	=2	=2
4g	D,	H,	L,	P,	T,	X,	Z,
8r	.	.	.	.	.	.	.
=3	=3	=3	=3	=3	=3	=3	=3
8g	wenn	w&auml;rst	Aeug-	gleich	Schei-	mach'	nun
8f	ich	du	-lein	ei-	-den	ei-	geh'
8g	dich	doch	so	-ner	thut	-nen	zu
=4	=4	=4	=4	=4	=4	=4	=4
4a	seh',	da!	hell	Fee	weh.	Knix,	Bett!
8r	.	.	.	.	.	.	.
=5	=5	=5	=5	=5	=5	=5	=5
*-	*-	*-	*-	*-	*-	*-	*-
!!!SMS: Deutscher Liederschatz, Band 1, Ludwig Erk, ed.
</script>
