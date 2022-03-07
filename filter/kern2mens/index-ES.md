---
title: filtro kern2mens
lang: en es
ref: filters-kern2mens
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 10 May 2018
translation_date: 8 Aug 2021
last_updated: 10 May 2018
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/kern2mens/index-ES.html
---
El [filtro](/filter/) _kern2mens_ puede utilizarse para convertir los datos `**kern` (notación musical occidental moderna) en `**mens` (notación mensural blanca).

He aquí un ejemplo de uso de kern2mens para convertir la notación moderna en notación mensural blanca:
s

{% include verovio.html
	source="example1"
	scale="60"
	pageWidth="1100"
	humdrum-min-width="250"
%}

<script type="application/x-humdrum" id="example1">
!!!filter: kern2mens
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>

Prueba a eliminar la primera línea de datos que comienza con `!!!filter:`` para ver la notación moderna original.  Prueba también a copiar y pegar los datos anteriores en el editor de texto [VHV](http://verovio.humdrum.org/?k=e).

Consulta la página de documentación [while mensural notation](/humdrum/mens) para obtener más información sobre la representación `**mens`.

En [VHV](http://verovio.humdrum.org) (pero no en esta página), puedes ver los datos convertidos de `**mens` escribiendo [alt-c](/commands/alt-c) para compilar el filtro.  Para el ejemplo anterior, esto producirá datos que se parecen al siguiente ejemplo:


{% include verovio.html
	source="example1b"
	scale="60"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example1b">
**mens
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
siF
SiA
.
siF
=3-
siB-
siG
=4-
siG
sp:A
.
MiG
siF
=6-
SiE
=7-
siF
SiA
.
siF
=9-
siB-
siG
=10-
siG
sp:A
.
miG
miF
siG
=12-
SiF
=17-
siF
Sic
.
sie-
=19-
Sid
=20-
sic
siA
=21-
siB-
siG
=22-
SiF
=23-
siF
Sic
.
sie-
=27-
Sid
=28-
sic
siA
=29-
siB-
siG
=30-
SiF
=||
*-
</script>



{% include note.html
	content=" Los datos convertidos pueden no ser completamente correctos desde el punto de vista sintáctico y pueden requerir una edición adicional &mdash; como la eliminación de puntos de perfección en las mediciones de círculos (esto se mejorará en el futuro).  El filtro kern2mens todavía está en modo de desarrollo, así que espera errores.  Por ejemplo, el primer E4 (línea superior) debería ser bemol, y el segundo debería tener un bemol editorial encima."
%}

## Ajuste de la clave ##
Un futuro desarrollo permitirá especificar una "clave original" en la notación moderna que se utilizará en los datos de `**mens`.  Dicha clave sería como una clave normal de `**kern`, pero con una `o` antepuesta a la "clave", como por ejemplo `*oclefC3` para una clave de contralto.  Actualmente, la opción `-c` puede utilizarse para cambiar la clave entre la visualización de la notación `**kern` y `**mens`.  Aquí está la misma música de arriba, pero poniendo la clave de "mens" en C3 desde la línea de filtro:


{% include verovio.html
	source="example2"
	scale="60"
	humdrum-min-width="250"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example2">
!!!filter: kern2mens -c C3
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>
De forma similar a `*oclef`, habrá una implementación de signos de "mensuración original", como `*omet(C|)`.  Este signo de mensuración se utilizará preferentemente sobre el signo de tiempo o un signo de mensuración simple "met(c|)" cuando se convierta en datos `**mens`.

## Barras de compás ##
Las líneas de compás siguen siendo necesarias en los datos convertidos para que Verovio pueda dividir la música en varias líneas.  Fíjate en que las notas ligadas se fusionan en notas simples en la conversión.  Cualquier línea de compás que divida una nota será eliminada, pero el resto se dejará para propósitos de diseño.  Puedes eliminar las líneas de compás añadiendo la opción `-M`, pero actualmente sólo es útil para ejemplos cortos de una sola línea. 

Si quieres eliminar los números de compás de los compases, añade la opción `-N` al filtro. Si quieres ver las líneas de compás restantes, añade la opción `-I`. Este es un ejemplo de uso de las opciones `-N` y `-I` al mismo tiempo:

{% include verovio.html
	source="example2b"
	scale="60"
	humdrum-min-width="250"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example2b">
!!!filter: kern2mens -c C3 -NI
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>

Obsérvese que se han eliminado algunas líneas de compás para evitar las notas ligadas en los datos convertidos de `**mens`.

## Texto ##
El texto subyacente (es decir, la letra de la música) puede darse como una columna `**text` a la derecha de la columna  `**kern` y de la columna resultante `**mens`:

{% include verovio.html
	source="example-text"
	scale="40"
	tabsize="12"
	humdrum-min-width="250"
	pageWidth="1200"
%}

<script type="application/x-humdrum" id="example-text">
!!!filter: kern2mens -cC1 -N
**kern	**text
*staff1	*staff1
*Ivox	*
*I"Superius	*
*I'S	*
*clefG2	*
*k[]	*
*M2/1	*
*met(C|)	*
=8	=8
0b	Dul-
=9	=9
0cc	-ces
=10	=10
1.cc	ex-
4b	.
4a	.
=11	=11
1a	-u-
[1cc	-vi-
=12	=12
2cc]	.
4b	.
4cc	.
2b	.
[2a	.
=13	=13
2a]	.
2cc	.
2b	.
4a	.
4g	.
=14	=14
2a	.
2g	.
1f	.
=15	=15
0e	-e
=16	=16
0r	.
=17	=17
1b	dum
1dd	.
=18	=18
0cc	fa-
=19	=19
0b	-ta
=20	=20
1e	de-
[1f	-us-
=21	=21
0f]	.
=22	=22
1e	-que
1g	si-
=23	=23
0f	-ne-
=24	=24
0e	-bant,
=25	=25
0g	ac-
=26	=26
1f	-ci-
2e	-pi-
2g	.
=27	=27
2f	-te
1e	hanc
2g	.
=28	=28
4f	a-
4e	.
4d	.
4c	.
1d	-ni-
=29	=29
1c	-mam,
1r	.
=30	=30
1cc	me-
1b	-que
=31	=31
1b	hi-
2a	-is
2g	.
=32	=32
2r	.
2a	ex
2g	sol-
2cc	.
=33	=33
2b	-vi-
1a	.
2g#i	.
=34	=34
1a	-te
1a	cu-
=35	=35
1.dd	.
2cc	.
=36	=36
2b	.
2a	.
2g	.
2f	.
=37	=37
2e	.
2d	.
2g	.
[2f	.
=38	=38
4f]	.
4e	.
1e	.
2d	.
=39	=39
0e	-ris.
=40	=40
[0a	Vi-
=41	=41
0a]	.
=42	=42
0g	-xi
=43	=43
=45	=45
0r	.
=46	=46
0dd	et,
=47	=47
1cc	que
2cc	de-
2cc	-de-
=48	=48
1b	-rat
1a	cur-
=49	=49
0dd	-sum
=50	=50
1r	.
1g	for-
=51	=51
0cc	-tu-
=52	=52
1b	.
[1a	-na,
=53	=53
1a]	.
1g	pe-
=54	=54
1.f#	-re-
4e	.
4f#i	.
=55	=55
1g	-gi,
1r	.
=56	=56
[0c#	et
=57	=57
0c#]	.
=58	=58
[0f	nunc
=59	=59
1f]	.
1d	.
=60	=60
1.g	ma-
4f	.
4e	.
=61	=61
1g	.
1f	.
=62	=62
2e	-gna
1e	me-
2d	.
=63	=63
1e	-i
1r	.
=64	=64
0r	.
=65	=65
[0b	sub
=66	=66
0b]	.
=67	=67
1.cc	ter-
4b	.
4a	.
=68	=68
0g#	-ras
=69	=69
1r	.
1cc	i-
=70	=70
2b	.
2a	.
1g	-bit
=71	=71
2a	i-
2cc	.
2b	.
2a	.
=72	=72
2g	-ma-
2.dd	.
4cc	.
4b	.
4a	.
=73	=73
2g	.
2cc	.
2b	.
2a	.
=74	=74
2g	.
2.a	.
4g#i	.
4g#i	.
4f#i	.
=75	=75
0al	-go.
==	==
*-	*-
</script>

## Creación de PDFs ##
En [VHV](http://verovio.humdrum.org), puedes ajustar el tamaño de la ventana para que se ajuste a la música y, a continuación, escribir [alt-t](/commands/alt-t) para descargar un archivo PDF de una página con la música visible:


{% include image.html
	file="vhvview.png"
	caption="Ajusta el tamaño de las ventanas para que la música quede completamente a la vista."
%}

Aquí está el [archivo PDF resultante](score.pdf), y abajo se muestra el archivo PDF visto en un visor de PDF:

{% include image.html
	file="score.png"
	caption="Descarga de un archivo PDF de una página en un visor de PDF."
%}

Para partituras más largas, escriba [alt-shift-T](/commands/alt-t) para generar una partitura PDF de varias páginas con formato para papel de tamaño carta.

## Conversión de partituras polifónicas ##


También se pueden convertir obras polifónicas:


{% include verovio.html
	source="example-poly"
	scale="30"
	humdrum-min-width="650"
	tabsize="12"
	pageWidth="1800"
%}

<script type="application/x-humdrum" id="example-poly">
!!!filter: kern2mens -N
**kern	**kern	**kern	**kern
*Ivox	*Ivox	*Ivox	*Ivox
*I"Bassus	*I"Tenor	*I"Altus	*I"Discantus
*I'B	*I'T	*I'A	*I'D
*staff4	*staff3	*staff2	*staff1
*clefF4	*clefC4	*clefC3	*clefC1
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-	=1-
0r	0r	1r	1d
.	.	1G	2d
.	.	.	2d
=2	=2	=2	=2
0r	0r	2G	1g
.	.	2G	.
.	.	1c	2g
.	.	.	[2a
=3	=3	=3	=3
0r	0D	2d	4a]
.	.	.	4g
.	.	4c	4f
.	.	4B	4e
.	.	1A	2.f
.	.	.	4e
=4	=4	=4	=4
0GG	1D	2.G	1g
.	.	4A	.
.	1D	4B	2d
.	.	4c	.
.	.	2d	[2g
=5	=5	=5	=5
1GG	0G	2e	2g]
.	.	1c	4f
.	.	.	4e
1GG	.	.	1d
.	.	2B	.
=6	=6	=6	=6
0C	1r	1.c	1c
.	1G	.	1cc
.	.	4B	.
.	.	4A	.
=7	=7	=7	=7
1r	1B	2G	2.dd
.	.	1g	.
.	.	.	4cc
1C	1c	.	4b
.	.	.	4a
.	.	[2e	[2a
=8	=8	=8	=8
1E	1B	2e]	2a]
.	.	2e	2g
1F	1A	2.c	2a
.	.	.	[2cc
.	.	4d	.
=9	=9	=9	=9
1E	0r	4e	4cc]
.	.	4f	4b
.	.	1g	2g
1D	.	.	1a
.	.	2f#i	.
=10	=10	=10	=10
0r	1B	1g	1d
.	1c	2g	1r
.	.	[2e	.
=11	=11	=11	=11
1E	1B	2e]	1g
.	.	2e	.
1F	1A	2c	2a
.	.	[2d	2a
=12	=12	=12	=12
1E	1B	2d]	1g
.	.	2G	.
1D	1r	1A	1f
=13	=13	=13	=13
1E	1G	1G	2r
.	.	.	2g
1r	1A	[1c	2f
.	.	.	[2e
=14	=14	=14	=14
1C	1G	1c]	2e]
.	.	.	2g
1D	1r	2A	2f
.	.	2B	2d
=15	=15	=15	=15
1C	1E	1c	2g
.	.	.	4f
.	.	.	4e
1r	2F	2r	1d
.	2G	2d	.
=16	=16	=16	=16
1AA	1A	2e	1c
.	.	2c	.
2BB	2r	2d	2f
2C	2G	4c	[2e
.	.	4B	.
=17	=17	=17	=17
1D	1F	1A	2e]
.	.	.	1d
2r	1E	1G	.
2C	.	.	[2g
=18	=18	=18	=18
1BB	1D	2r	4g]
.	.	.	4f
.	.	1G	4e
.	.	.	4d
1AA	1r	.	1c
.	.	2F#i	.
=19	=19	=19	=19
1GG	1d	0G	1r
1r	2d	.	1dd
.	2d	.	.
=20	=20	=20	=20
1G	1B	2r	2dd
.	.	1d	2dd
2G	1G	.	1b
2G	.	[2B	.
=21	=21	=21	=21
1E	1r	2B]	2g
.	.	1e	2.cc
1C	[1c	.	.
.	.	.	4b
.	.	[2e	4a
.	.	.	4g
=22	=22	=22	=22
1r	2c]	2e]	2a
.	2B	2d	2g
[1F	2A	[1c	2a
.	2G	.	[2cc
=23	=23	=23	=23
2F]	0A	1c]	4cc]
.	.	.	4b
2E	.	.	4a
.	.	.	4g
2D	.	2d	2f
2C	.	2e	2g
=24	=24	=24	=24
0D	2D	0d	2f
.	2B	.	1g
.	1A	.	.
.	.	.	2f#i
=25	=25	=25	=25
0GGl	0Gl	0dl	0gl
==	==	==	==
*-	*-	*-	*-
</script>

{% include warning.html
	content="Actualmente existe un error con las obras polifónicas que contienen texto."
%}


### Extracción de partes de una partitura polifónica ###
Utiliza el [filtro extract](/filter/extract) para seleccionar una parte de una partitura `**kern` antes de convertirla en notación mensural.   El siguiente ejemplo utiliza dos filtros en serie:

```
!!!filter: extract -k 2
!!!filter: kern2mens -N
```
El primer filtro extrae la segunda columna de kern de la izquierda, que es la parte de tenor, y luego convierte esa parte en notación mensural.  Los dos filtros también pueden fusionarse en una sola línea colocando un carácter tubería entre ellos:

```
!!!filter: extract -k 2 | kern2mens -N
```


{% include verovio.html
	source="example-poly2"
	scale="60"
	humdrum-min-width="650"
	tabsize="12"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example-poly2">
!!!filter: extract -k 2
!!!filter: kern2mens -N
**kern	**kern	**kern	**kern
*Ivox	*Ivox	*Ivox	*Ivox
*I"Bassus	*I"Tenor	*I"Altus	*I"Discantus
*I'B	*I'T	*I'A	*I'D
*staff4	*staff3	*staff2	*staff1
*clefF4	*clefC4	*clefC3	*clefC1
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-	=1-
0r	0r	1r	1d
.	.	1G	2d
.	.	.	2d
=2	=2	=2	=2
0r	0r	2G	1g
.	.	2G	.
.	.	1c	2g
.	.	.	[2a
=3	=3	=3	=3
0r	0D	2d	4a]
.	.	.	4g
.	.	4c	4f
.	.	4B	4e
.	.	1A	2.f
.	.	.	4e
=4	=4	=4	=4
0GG	1D	2.G	1g
.	.	4A	.
.	1D	4B	2d
.	.	4c	.
.	.	2d	[2g
=5	=5	=5	=5
1GG	0G	2e	2g]
.	.	1c	4f
.	.	.	4e
1GG	.	.	1d
.	.	2B	.
=6	=6	=6	=6
0C	1r	1.c	1c
.	1G	.	1cc
.	.	4B	.
.	.	4A	.
=7	=7	=7	=7
1r	1B	2G	2.dd
.	.	1g	.
.	.	.	4cc
1C	1c	.	4b
.	.	.	4a
.	.	[2e	[2a
=8	=8	=8	=8
1E	1B	2e]	2a]
.	.	2e	2g
1F	1A	2.c	2a
.	.	.	[2cc
.	.	4d	.
=9	=9	=9	=9
1E	0r	4e	4cc]
.	.	4f	4b
.	.	1g	2g
1D	.	.	1a
.	.	2f#i	.
=10	=10	=10	=10
0r	1B	1g	1d
.	1c	2g	1r
.	.	[2e	.
=11	=11	=11	=11
1E	1B	2e]	1g
.	.	2e	.
1F	1A	2c	2a
.	.	[2d	2a
=12	=12	=12	=12
1E	1B	2d]	1g
.	.	2G	.
1D	1r	1A	1f
=13	=13	=13	=13
1E	1G	1G	2r
.	.	.	2g
1r	1A	[1c	2f
.	.	.	[2e
=14	=14	=14	=14
1C	1G	1c]	2e]
.	.	.	2g
1D	1r	2A	2f
.	.	2B	2d
=15	=15	=15	=15
1C	1E	1c	2g
.	.	.	4f
.	.	.	4e
1r	2F	2r	1d
.	2G	2d	.
=16	=16	=16	=16
1AA	1A	2e	1c
.	.	2c	.
2BB	2r	2d	2f
2C	2G	4c	[2e
.	.	4B	.
=17	=17	=17	=17
1D	1F	1A	2e]
.	.	.	1d
2r	1E	1G	.
2C	.	.	[2g
=18	=18	=18	=18
1BB	1D	2r	4g]
.	.	.	4f
.	.	1G	4e
.	.	.	4d
1AA	1r	.	1c
.	.	2F#i	.
=19	=19	=19	=19
1GG	1d	0G	1r
1r	2d	.	1dd
.	2d	.	.
=20	=20	=20	=20
1G	1B	2r	2dd
.	.	1d	2dd
2G	1G	.	1b
2G	.	[2B	.
=21	=21	=21	=21
1E	1r	2B]	2g
.	.	1e	2.cc
1C	[1c	.	.
.	.	.	4b
.	.	[2e	4a
.	.	.	4g
=22	=22	=22	=22
1r	2c]	2e]	2a
.	2B	2d	2g
[1F	2A	[1c	2a
.	2G	.	[2cc
=23	=23	=23	=23
2F]	0A	1c]	4cc]
.	.	.	4b
2E	.	.	4a
.	.	.	4g
2D	.	2d	2f
2C	.	2e	2g
=24	=24	=24	=24
0D	2D	0d	2f
.	2B	.	1g
.	1A	.	.
.	.	.	2f#i
=25	=25	=25	=25
0GGl	0Gl	0dl	0gl
==	==	==	==
*-	*-	*-	*-
</script>




## Conversión mediante URL ##
El filtro _kern2mens_ puede añadirse a la URL de VHV para que se ejecute automáticamente sobre los datos colocados en el editor de texto.  Esto también permitirá la conversión directa a la notación mensural desde un archivo MusicXML arrastrado y soltado en la página:

[verovio.humdrum.org/?filter=kern2mens](http://verovio.humdrum.org/?filter=kern2mens&k=e)

Para añadir espacios a la URL, utiliza `%20` en lugar del espacio.  Por ejemplo, esta es la URL del filtro `kern2mens -N`:

[verovio.humdrum.org/?filter=kern2mens%20-N](http://verovio.humdrum.org/?filter=kern2mens%20-N&k=e)

Haz clic en una de las líneas anteriores, y luego intenta arrastrar y soltar una partitura MusicXML en la página.  Esto convertirá automáticamente los datos MusicXML en datos Humdrum, y luego el filtro URL convertirá los datos `**kern` en datos `**mens`.  Para ver los datos finales de `**mens`, escribe [alt-c](/commands/alt-c) para compilar el filtro y mostrar el resultado en el editor de texto.


## Tareaas pendientes ##
Algunas cosas en las que trabajar: combinar los silencios de breve y longa, y los silencios de longa con los de máxima.  Actualmente esto tiene que hacerse a mano después de la conversión a `**mens`.  

Como se ha mencionado anteriormente, las alteraciones y las alteraciones editoriales aún necesitan ser trabajadas.  

Además, hay que abordar la supresión de los puntillos en las mensuraciones perfectas (actualmente hay que hacerlo a mano).  

Otras características, como la coloración y las alteraciones, no se abordan, y las ligaduras tienen que anotarse a mano después de convertirlas en datos de `**mens'.

El filtro rscale debería implementarse para permitir la notación moderna no reducida.





