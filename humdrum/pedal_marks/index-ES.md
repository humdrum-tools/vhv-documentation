---
title: Marcas de pedal
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-pedal_marks
keywords: humdrum pedal marks
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Descripción de la codificación de las marcas de pedal en las columnas `**kern`
sidebar: main_sidebar
permalink: /humdrum/pedal_marks/index-ES.html
---


Las marcas de pedal de sostenido pueden codificarse en los datos Humdrum `**kern` utilizando `*ped` para indicar una marca de inicio de pedal y `*Xped` para indicar una marca de fin de pedal:

{% include verovio.html
	source="pedal"
	tabsize="12"
	humdrum-min-height="600px"
%}

<script type="application/json" id="pedal">
**kern	**kern
*clefF4	*clefG2
*k[]	*k[]
*M3/4	*M3/4
=33	=33
*ped	*
4FF'	(8ccL
.	8ff
4A 4c 4f	8gg
.	8aa
4A 4c 4f	8ccc
.	8fffJ
*Xped	*
=34	=34
*ped	*
4BB'	8gggL
.	8aaa
4G 4d 4f	8ggg
.	8fff
4G 4d 4f	8eee
.	8dddJ)
*Xped	*
=35	=35
*ped	*
4C'	(12cccL
.	12ddd
.	12cccJ
4G 4c 4e	4gg')
4G 4c 4e	(8ggL
*Xped	*
.	8bbnJ
=36	=36
*ped	*
4F'	2aa
4A 4c 4f	.
4A 4c 4f	4ff)
.	.
*Xped	*
=37	=37
4A 4c 4e	(8ccL
.	8cccJ
4A 4c 4e	12bbL
.	12ccc
.	12bbJ
4A 4c 4f	8aaL
.	8ffJ
=38	=38
4B 4f	8dd'L)
.	8dd'J
.	(8qee/
4B 4f	4dd)
4c 4e	4cc^
=39	=39
*-	*-
</script>


Prueba a añadir o quitar marcas de pedal arriba/abajo en los datos de Humdrum anteriores para ver cómo cambia la notación de la derecha.


Las marcas de pedal pueden añadirse gráficamente en VHV haciendo clic en una nota y pulsando <span class="keypress">alt-p</span> para añadir una marca de inicio de pedal o <span class="keypress">alt-shift-P</span> para añadir una marca de fin de pedal.


