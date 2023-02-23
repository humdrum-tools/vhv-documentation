---
title: Trinos
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-trills
keywords: humdrum trill
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar los trinos en las columnas **kern.
sidebar: main_sidebar
permalink: /humdrum/trills/index-ES.html
---

Los trinos se codifican en columnas `**kern` utilizando marcadores `T` o `t` en los tokens de las notas:

{% include verovio.html
	source="trill1"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="application/json" id="trill1">
**kern
2cT
2dT
2et
2fT
2gT
2aT
2bt
*-
</script>

El intervalo utilizado en el trino se indica con la letra: la `T` mayúscula indica que el intervalo del trino es una segunda mayor, mientras que la `t` minúscula indica una segunda menor.

Cuando la alteración cromática de la nota auxiliar del trino no está en la armadura o en el estado actual para el tono diatónico dado, entonces se da una alteración para la nota auxiliar por encima de la marca de trino:

{% include verovio.html
	source="trill2"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="trill2">
**kern
*k[]
2ct
2dt
2eT
2ft
2gt
2at
2bT
*-
</script>

Observa en el ejemplo anterior que cualquier alteración en una nota auxiliar de trino se cancelará si una nota primaria siguiente está en el mismo tono diatónico pero con una alteración cromática diferente.  Por ejemplo, el segundo trino menor en Do bemol (la primera nota del ejemplo anterior) está en Re bemol. Dado que la nota siguiente es un Re natural, se suele añadir una alteración de cancelación a la nota para evitar interpretarla como un R bemol.  Para ocultar las alteraciones naturales en el ejemplo anterior, añade `ny` a las notas para ocultar los becuadros:

{% include verovio.html
	source="trill3"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="trill3">
**kern
*k[]
2ct
2dnyt
2enyT
2fnyt
2gnyt
2anyt
2bnyT
*-
</script>

El carácter `n` significa que la nota tiene una alteración natural, y el carácter `y` significa que el becuadro no debe mostrarse.


## Extensiones de línea ##

Si se duplica el carácter de trino en el token, se añadirá una línea de extensión al trino.

{% include verovio.html
	source="trill4"
	humdrum-min-height="220px"
	scale="55"
%}
<script type="application/json" id="trill4">
**kern
*k[]
*M4/4
=1
1cTT
=2
1ett
=3
1gTT
=
*-
</script>


Para continuar la extensión de la línea a lo largo de varias notas, utiliza dos caracteres de trino para comenzar el trino con una extensión de línea, y luego utiliza tres caracteres de trino en cada nota que debe estar bajo la misma extensión de línea de trino.

{% include verovio.html
	source="trill5"
	humdrum-min-height="330px"
	pageWidth="1000"
	scale="55"
%}
<script type="application/json" id="trill5">
**kern
*k[]
*M4/4
[2ett
=1
2ettt]
4f
[4gTT
=2
1g_TTT
=3
2gTTT
2g#TTT
=5
2a
*-
</script>

Las notas bajo la línea de trino no tienen que estar todas ligadas, como lo demuestra el primer Sol en el compás tres del ejemplo anterior.  Además, el siguiente Sol sostenido se incluye bajo la línea de extensión del trino aunque no sea la misma clase de tono que la nota que inició el trino. 

Cuando se codifican los trinos en la segunda subcolumna, las marcas de trino y las líneas se colocan automáticamente debajo del pentagrama:


{% include verovio.html
	source="trill6"
	humdrum-min-height="330px"
	scale="55"
%}
<script type="application/json" id="trill6">
**kern
*k[]
*M4/4
=1
[1cTT
=
2cTTT]
=2
*^
4aT	[1cTT
[4gTT	.
2gTTT_	.
=3	=3
1gTTT]	1cTTT]
*v	*v
=
*-
</script>


