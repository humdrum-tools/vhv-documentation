---
title: Notas guía
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-cues
keywords: humdrum cue
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar las notas guía en las columnas de **kern.
sidebar: main_sidebar
permalink: /humdrum/cues/index-ES.html
---

Las notas guía son más pequeñas que las notas normales, similares a las notas de ornamento; sin embargo, a diferencia de estas últimas las notas guía poseen duraciones de partitura distintas de cero.  Las notas guía pueden ser codificadas de dos maneras dentro de las columnas `**kern`.  Para las notas guía ocasionales, se puede añadir un registro RDF para marcar las notas individuales como notas guía:


{% include verovio.html
	source="cue1"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="cue1">
**kern
4e
*^
4g	8gN\L
.	8aNJ
*v	*v
4b
=
*-
!!!RDF**kern: N = cue size
</script>


Para generar una secuencia más larga de notas guía, se puede utilizar un segundo método que utiliza interpretaciones tándem `*cue` y `*Xcue` para activar/desactivar el cambio de tamaño:

{% include verovio.html
	source="cue2"
	humdrum-min-height="580px"
	tabsize="12"
	scale="55"
%}
<script type="application/json" id="cue2">
**kern	**kern
*clefF4	*clefG2
*M3/4	*M3/4
=	=
*	*Xtuplet
*	*cue
*	*rscale:2
4G 4c 4f	(>20ddL>
.	20ee
.	20dd
.	20cc#
.	20dd
4G 4B 4f	20dd#
.	20ee
.	20ff
.	20ff#
.	20gg
4G 4B 4f	20gg#
.	20bb
.	20aa
.	20ggn
.	20ffnJ)
*	*Xcue
*	*rscale:1
=	=
4G 4B 4e	2.ee
4G 4B 4e	.
4G 4B 4e	.
=	=
*-	*-
!!!RDF**kern: > = above
</script>


Los marcadores `*cue` y `*Xcue` sólo se aplican a una subcolumna específica de la música, por lo que una subcolumna puede ser de notas guía mientras que otra no.  Esto es útil para añadir notas guía a partes de la orquesta.


{% include verovio.html
	source="cue3"
	humdrum-min-height="710px"
	scale="55"
%}
<script type="application/json" id="cue3">
**kern
*M4/4
=1
*^
*	*cue
!	!LO:TX:b:t=vlas.
1r	4e
.	4f
.	4e
.	4c
*	*Xcue
=2	=2
*cue	*
!LO:TX:a:t=vlns.	!
4ee	1r
4ff	.
4ee	.
4cc	.
*Xcue	*
=3	=3
*cue	*
8ffL	2r
8eeJ	.
8ddL	.
8ccJ	.
!	!LO:TX:a:B:t=solo
2ryy	16ffLL
.	16ee
.	16dd
.	16ccJJ
.	16bLL
.	16a
.	16g
.	16fJJ
*Xcue	*
*v	*v
=
*-
</script>


