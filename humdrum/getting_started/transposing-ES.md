---
title: tutorial de codificación de transposición
lang: en es
ref: humdrum-getting_started-transposing
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial transposing
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar la transposición básica en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/transposing-ES.html
---

<!--{% include humdrum/transposing.txt %}-->

## Instrumentos transpositores ##

Las partituras de instrumentos transpositores siempre se codifican en el tono de concierto en los datos de Humdrum, y las instrucciones para la transposición al tono escrito se codifican al principio de la parte.  En el siguiente ejemplo, la segunda columna codifica una parte de clarinete en Si bemol, con la interpretación de transposición `*ITrd1c2` que significa que la parte escrita está un tono diatónico arriba, equivalente a 2 semitonos arriba.

{% include verovio.html
	humdrum-min-height="340px"
	source="transpose1"
	tabsize="10"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="transpose1">
**kern	**kern
*I"Cello	*I"Clar. in Bb
*	*ITrd1c2
*clefF4	*clefG2
*M4/4	*M4/4
*k[]	*k[]
=1	=1
4C	4c
4D	4d
4E	4e
4F	4f
=2	=2
4G	4g
4A	4a
4B	4b
4c	4cc
==	==
*-	*-
</script>

Consulta la sección [instrumentos transpositores](/humdrum/transposing) de la documentación para obtener más información.



