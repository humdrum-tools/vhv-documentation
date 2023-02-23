---
title: Instrumentos transpositores
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-transposing
keywords: humdrum transposing parts
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar los instrumentos transpositores en las partituras de Humdrum.
sidebar: main_sidebar
permalink: /humdrum/transposing/index-ES.html
---


Las partituras siempre se escriben en tono sonoro.  Si quieres poder mostrar una partitura de un instrumento transpositor, entonces añade información de transposición a cada parte que transpongas.  Una interpretación transpositora comienza con la cadena `*ITr` seguida de la descripción diatónica/cromática del intervalo necesario para producir la partitura escrita.  Por ejemplo, un instrumento en Si bemol necesita ser escrito subiendo una segunda mayor desde su tono de concierto.  Esto significa subir un tono diatónico, o subir dos semitonos cromáticos.  Por tanto, la interpretación final de la transposición es `*ITrd1c2`.  Para un instrumento en Fa, la transposición sería subir 4 pasos diatónicos, lo que equivale a 7 semitonos para una interpretación de `*ITrd4c7`.

{% include verovio.html
	source="transpose"
	humdrum-min-height="560px"
	scale="55"
	tabsize="10"
	pageWidth="1000"
%}

<script type="application/json" id="transpose">
**kern	**kern	**kern
*part3	*part2	*part1
*staff3	*staff2	*staff1
*I"in C	*I"in F	*I"in Bb
*clefF4	*clefG2	*clefG2
*	*ITrd4c7	*ITrd1c2
*k[b-e-]	*k[b-]	*k[b-e-]
*M3/4	*M3/4	*M3/4
*MM120	*MM120	*MM120
4r	4r	4ee-
=1	=1	=1
2.r	2.r	4dd
.	.	4cc
.	.	4b-
=2	=2	=2
2.r	4r	4a
.	.	8qcc
.	4r	4b-
.	4c	4a
=3	=3	=3
2GG	4B-	2.g
.	4A	.
4r	4G	.
=4	=4	=4
2.r	4F#	4a
.	4G	4b-
.	4F	4b 4aa-
=5	=5	=5
2C	4E-	4cc 4gg
.	4r	4ff
4r	4r	4ee-
=6	=6	=6
2GG 2G	4f 4g	4dd
.	.	8qff
.	4r	4ee-
4r	4f	4dd
=7	=7	=7
2C	4e-	4cc
.	4d	4r
4r	4c	4r
=8	=8	=8
2.r	4BX	4dd
.	4c	4ee-
.	4B-	4dd- 4een 4gg
=9	=9	=9
2FF	4A	4cc 4ff
.	4G	4b- 4ee-
4r	4F	4a 4dd
=10	=10	=10
4r	4E-	4g 4cc
.	.	8qee-
4r	4F	4a 4dd
[4FF	4E-	4g 4cc
=11	=11	=11
*	*	*^
4FF]	4D	2.b-	4f
4EE- 4E-	4r	.	4g
4DD 4D	4r	.	4f
*	*	*v	*v
=12	=12	=12
4CC 4C	4r	2e- 2f# 2a
8qEE-\	.	.
4DD 4D	4r	.
4CC 4C	4f#	4ee-
=13	=13	=13
4BBB- 4BB-	4g	4dd
4AAA 4AA	4f#	4cc
4GGG 4GG	4g	4b-
=14	=14	=14
*	*	*^
2CC 2C	2e-	4a	2g
.	.	8qcc\	.
.	.	4b-	.
4DD 4D	4c	4a	4f#
*	*	*v	*v
=15	=15	=15
2.GG	2.B-	2.d 2.g
==	==	==
*-	*-	*-
</script>

En la partitura de ejemplo anterior, la segunda parte simula una parte de trompa en la tonalidad de Fa, pero típicamente con una parte de trompa, no hay signatura de la tonalidad y se omite en la partitura (de lo contrario debería mostrar un Si bemol en la armadura).

Cuando se reproduce una partitura que contiene instrumentos transpositores en VHV, la conversión MIDI será una partitura sonora.

## Importación de MusicXML ##

Los archivos MusicXML que contengan partes transpuestas se manejarán correctamente cuando los archivos se conviertan en datos de Humdrum arrastrando y soltando los archivos en la página web de VHV.  Las notas se transponen de la afinación escrita a la afinación sonora durante el proceso de conversión.

Intenta descargar [este archivo](Transposing.xml), que contiene la partitura de ejemplo en formato MusicXML, y luego arrástrala al editor VHV.

## Exportación de MEI ##

Al convertir en datos MEI, las notas se almacenan en forma transpuesta, y la cabecera de cada parte contiene la información de transposición para convertirla en tono sonoro (por lo que una parte escrita para un instrumento en Si bemol se transpondría un tono diatónico igual a dos semitonos hacia abajo para producir los tonos sonoros).



