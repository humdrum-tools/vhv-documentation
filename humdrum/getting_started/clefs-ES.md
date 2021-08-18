---
title: tutorial de codificación de claves
lang: en es
ref: humdrum-getting_started-clefs
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial clefs
creation_date: 27 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar claves en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/clefs-ES.html
---

<!--{% include humdrum/clefs.txt %}-->

## Claves ##

VHV elegirá automáticamente la clave más adecuada (ya sea grave o aguda) para ajustarse al rango de alturas de las notas en un pentagrama, pero normalmente se codifica una clave explícitamente para la música.  Las claves se codifican en *tokens de interpretación* que comienzan con un único `*` seguido de la cadena `clef` y, a continuación, la forma y la posición de la línea de la clave.  Por ejemplo, una clave de Sol es "clefG2", donde "G" significa una clave de Sol y "2" significa que la clave está centrada en la segunda línea desde la parte inferior del pentagrama.  La clave de Fa es `*clafF4` ya que es una clave de Fa en la cuarta línea del pentagrama.

{% include verovio.html
	source="clef1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="clef1">
**kern
*clefG2
1c
*clefF4
1c
*clefC3
1c
*-
</script>

Intenta mover las claves a diferentes líneas del pentagrama cambiando el número después de la forma de la clave en el cuadro de texto del ejemplo anterior.

Una clave de tenor se representa con `*clefGv2`, donde la `v` significa que la música debe tocarse una octava más baja que los tonos que suenan en la clave normal.  Intenta crear una clave de tenor en el ejemplo interactivo anterior. El operador `v` también funciona en las otras claves (pero este tipo de claves son muy raras).  Otra clave rara es `*clefG^2` que es lo contrario de `*clefGv2`, donde la música se escribe una octava más baja que el tono que suena realmente para la forma normal de la clave.  También puede intentar crear claves exóticas de dos octavas duplicando los marcadores `^^` y `vv`.





