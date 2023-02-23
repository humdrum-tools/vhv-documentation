---
title: Grupos de valoración especial
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-tuplet_styling
keywords: humdrum tuplet styling
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Los números visualizados de los grupos irregulares pueden activarse o desactivarse para una columna.
sidebar: main_sidebar
permalink: /humdrum/tuplets/index-ES.html
---


La notación musical que contiene muchos grupos artificiales suele omitir los números de los grupos después de las primeras ocurrencias de los mismos cuando la interpretación rítmica sin el número sigue siendo clara.  A continuación se muestra un ejemplo de números de tresillos omitidos en el primer movimiento de la sonata *Claro de Luna* de Beethoven.  Sólo el primer compás contiene números de tresillos visibles, y los siguientes no están marcados:

{% include image.html
	file="moonlight.gif"
	alt="moonlight sonata mvmt 1, mm 1-8"
	max-width="100%"
	caption="Beethoven, Sonata Claro de Luna, mvmt.1, mm. 1&ndash;8."
%}

Para desactivar los números de grupo irregular en una columna de Humdrum `**kern`, añade la interpretación tándem `*Xtuplet` en algún lugar delante de la primera nota del grupo que debería tener un número suprimido.  Para volver a mostrar los números de grupo irregular en la misma columna, añade la interpretación tándem `*tuplet`.

{% include verovio.html
	source="moonlight"
	scale="30"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="moonlight">
**kern	**kern
*clefF4	*clefG2
*k[f#c#g#d#]	*k[f#c#g#d#]
*c#:	*c#:
*M2/2	*M2/2
*MM54	*MM54
=1-	=1-
1CC# 1C#	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
*	*Xtuplet
=2	=2
1BBB 1BB	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
=3	=3
2AAA 2AA	12AL
.	12c#
.	12eJ
.	12AL
.	12c#
.	12eJ
2FFF# 2FF#	12AL
.	12dn
.	12f#J
.	12AL
.	12d
.	12f#J
=4	=4
2GGG# 2GG#	12G#L
.	12B#
.	12f#J
.	12G#L
.	12c#
.	12eJ
2GGG# 2GG#	12G#L
.	12c#
.	12d#XJ
.	12F#Lj
.	12B#
.	12d#J
=5	=5
*	*^
1CC# 1GG# 1C#	2r	12EL
.	.	12G#
.	.	12c#J
.	.	12G#L
.	.	12c#
.	.	12eJ
.	4r	12G#L
.	.	12c#
.	.	12eJ
!	!	!
.	8.g#L	12G#L
.	.	12c#
.	.	12eJ
.	16g#Jk	.
=6	=6	=6
1BBB# 1GG# 1BB#	2.g#	12G#L
.	.	12d#
.	.	12f#J
.	.	12G#L
.	.	12d#
.	.	12f#J
.	.	12G#L
.	.	12d#
.	.	12f#J
.	8.g#L	12G#L
.	.	12d#
.	.	12f#J
.	16g#Jk	.
=7	=7	=7
(<2CC# (>2C#	(2g#	12G#L
.	.	12c#
.	.	12eJ
.	.	12G#L
.	.	12c#
.	.	12eJ
2FFF#) 2FF#)	2a	12AL
.	.	12c#
.	.	12f#J
.	.	12AL
.	.	12c#
.	.	12f#J
=8	=8	=8
2BBB 2BB	2g#	12G#L
.	.	12B
.	.	12eJ
.	.	12G#L
.	.	12B
.	.	12eJ
2BBB 2BB	4f#	12AL
.	.	12B
.	.	12d#J
.	4b	12AL
.	.	12B
.	.	12d#J
=9	=9	=9
*	*v	*v
*-	*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

Prueba a mover o añadir las interpretaciones `*tuplet`/`*Xtuplet` en los datos anteriores de Humdrum para ver cómo afecta esto a la notación musical de la derecha.

{% include warning.html
	content="Una interpretación del estilo visual del grupo se aplica a toda una columna, y no puede controlarse de forma independiente dentro de las subcolumnas."
%}


## Estilo visual de grupos irregulares en la importación de MusicXML ##

Las interpretaciones `*tuplet`/`*Xtuplet` se pueden extraer de los datos MusicXML al convertirlos en datos Humdrum.  Adjunta cualquier expresión de texto que empiece por `*` a una nota o a un silencio, y se insertará una interpretación tándem antes de la nota.   A continuación se muestra un ejemplo de edición de música en MuseScore, donde los números de grupo de valoración especial se desactivan y se activan de nuevo:

{% include image.html
	file="musescore-tuplet.png"
	alt="Añadir interpretaciones de grupos irregulares en MuseScore"
	max-width="100%"
	caption="Añadir expresiones de texto para controlar el estilo de visualización de los números de grupos irregulares en MuseScore."
%}

Este <a target='_blank' href='tuplet.musicxml'>archivo MusicXML</a> arrastrado y soltado en [VHV](https://verovio.humdrum.org) producirá los siguientes datos de Humdrum que conservan las interpretaciones tándem incrustadas que controlan el estilo del número del grupo irregular.

{% include verovio.html
	source="musescore-tuplet"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="500px"
	tabsize="8"
%}
<script type="application/json" id="musescore-tuplet">
**kern
*clefG2
*k[]
*M4/4
=1
12ccL
12dd
12ccJ
12ddL
12cc
12ddJ
*Xtuplet
12ddL
12ee
12ddJ
12ccL
12dd
12ccJ
=2
12ddL
12cc
12ddJ
*tuplet
12ccL
12dd
12ccJ
12ddL
12cc
12ddJ
12ccL
12ee
12ddJ
==
*-
</script>



## Posicionamiento de los números de grupo irregular ##

El número del grupo irregular puede ajustarse por encima o por debajo del pentagrama utilizando un comando de disposición inmediatamente anterior a la nota que está al principio de un grupo irregular.


{% include verovio.html
	source="tupplace"
	scale="55"
	pageWidth="800"
	humdrum-min-height="350px"
	tabsize="8"
%}
<script type="application/json" id="tupplace">
**kern
*M4/4
=
12fL
12g
12aJ
!LO:TUP:b
12fL
12g
12aJ
12ffL
12ee
12ddJ
!LO:TUP:a
12ffL
12ee
12ddJ
=
*-
</script>




{% include warning.html
	content="La colocación de los números de los grupos irregulares todavía no es manejada de manera fina por subcolumnas.  Pero, en teoría, los números de grupo irregular no deberían ajustarse desde sus posiciones por defecto en estos casos."
%}




