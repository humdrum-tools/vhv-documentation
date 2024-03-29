---
title: Codificación de articulaciones
lang: en es
page_language: es
translator: David Rizo
translation_date: 17 Aug 2021
translation_update:
ref: humdrum-getting_started-articulations
keywords: humdrum encoding articulations
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Codificar las articulaciones en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/articulations/index-ES.html
---

<!--{% include humdrum/articulations.txt %}-->

## Articulaciones y ornamentos ##

Aquí hay un muestrario de articulaciones de notas:

{% include verovio.html
	humdrum-min-height="250px"
	source="artic1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic1">
**kern
4ff'
4ff^
4ff`
4ff~
4ff'~
4ff'^
4ff^^
4ff;
=
*-
</script>

Las articulaciones pueden colocarse en el lado opuesto de su ubicación automática añadiendo entradas RDF para forzar la articulación por encima o por debajo de la cabeza de nota:

{% include verovio.html
	humdrum-min-height="275px"
	source="artic2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic2">
**kern
4f'>
4ff^<
4f`>
4ff~<
4f'~>
4ff'^<
4f^^>
4ff;<
=
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


Aquí hay un muestrario de ornamentos.  Los ornamentos en mayúsculas indican notas auxiliares de un tono, y los ornamentos en minúsculas indican notas auxiliares de semitono.  Si las notas auxiliares requieren alteraciones en la notación musical gráfica, se añadirán automáticamente, así como las alteraciones de cortesía que puedan ser necesarias en las notas primarias que siguen a las notas auxiliares de los ornamentos. 

{% include verovio.html
	humdrum-min-height="250px"
	source="orn1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="orn1">
**kern
*M4/4
=1
2ct
2dT
=2
2fW
2gw
=
2fm
2gM
==
*-
</script>
