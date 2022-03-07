---
title: tutorial de codificación de texto
lang: en es
ref: humdrum-getting_started-text_directions
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial text directions
creation_date: 20 Aug 2017
translation_date: 18 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar texto en datos **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/text_directions-ES.html
---

<!--{% include humdrum/text_directions.txt %}-->

## Instrucciones para el texto ##

El texto puede mostrarse en la notación gráfica añadiendo una instrucción de diseño de texto a la codificación:


{% include verovio.html
	humdrum-min-height="360px"
	source="dir1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dir1">
**kern
*clefG2
*M4/4
=1
!LO:TX:b:i:t=cresc.
4c
2d
4f
=2
!LO:TX:a:i:t=accel.
4f
!LO:TX:b:t=comment
4d
4e
4c
==
*-
</script>

Los comentarios de disposición del texto comienzan con `!LO:TX:` y se colocan inmediatamente antes de la nota a la que se adjuntan.  El parámetro `a` significa colocar el texto arriba, y `b` significa colocar el texto abajo. El tipo de letra es romano por defecto; añadiendo el parámetro `i` el texto se pondrá en cursiva, y `b` en negrita.  El texto real viene dado por el parámetro `t`, como "*cresc.*" con el parámetro `t=cresc.`.  Tenga en cuenta que los parámetros se separan con dos puntos, y &amp;dos puntos; se utiliza para insertar dos puntos en la cadena de texto.



