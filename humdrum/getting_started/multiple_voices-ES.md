---
title: tutorial de codificación de voces múltiples
lang: en es
ref: humdrum-getting_started-multiple_voices
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial multiple voices
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar múltiples voces en un pentagrama en datos **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/multiple_voices-ES.html
---

<!--{% include humdrum/multiple_voices.txt %}-->


## Varias voces en un pentagrama ##

Los manipuladores de división de columna (`*^`) y los manipuladores de fusión de columna (`*v`) se utilizan para añadir o eliminar voces/capas en un pentagrama.  Ten en cuenta que la parte más alta del pentagrama es la que más se deja (al contrario de la ordenación del pentagrama de menor a mayor).

{% include verovio.html
	humdrum-min-height="210px"
	source="multi1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi1">
**kern
*M4/4
*^
2..gg	4b
.	4a
.	4g
.	4f
8ff	.
*v	*v
=
*-
</script>

Las notas que suenan juntas en las diferentes voces se colocan en la misma línea, y si la otra voz es sostenida, se utiliza un carácter `.` como marcador de posición para esa voz (el punto se denomina *token nulo* en la terminología de Humdrum).

### Capas/voces parciales ###

Las voces/capas que no continúan a lo largo del compás pueden codificarse de dos maneras equivalentes: (1) dividiendo y fusionando la columna según sea necesario en el compás, o (2) añadiendo silencios invisibles para rellenar la voz/capa durante todo el compás.  Para el método nº 1, ten en cuenta que la fusión de la columna no puede producirse hasta el final de las dos notas que suenan en cada capa.

{% include verovio.html
	humdrum-min-height="360px"
	source="multi2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi2">
**kern
*M4/4
=1
*^
2cc	4a
.	4g
*v	*v
4f
4e
=2
*^
2cc	4a
.	4g
2ryy	4f
.	4e
*v	*v
=
*-
</script>
