---
title: tutorial de codificación de barras de compás
lang: en es
ref: humdrum-getting_started-barlines
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial barlines
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar las barras de compás en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/barlines-ES.html
---

<!--{% include humdrum/barlines.txt %}-->

## Barlines ##

Las barras de compás se indican con un *token* que comienza con un signo de igual.  Un número opcional puede seguir inmediatamente al signo igual, representando un número de compás. VHV mostrará el número de compás en cada salto de línea/sistema, excluyendo la etiqueta para 
el compás&nbsp;1:

{% include verovio.html
	humdrum-min-height="525px"
	source="bar1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="bar1">
**kern
*clefG2
=1
1c
=2
1d
=3
1e
=4
1f
=5
1g
=6
1a
=7
1b
=8
1cc
=9
1dd
=10
1ee
=11
1ff
=12
1gg
=
*-
</script>


Después del número de compás puede haber un estilo opcional para la línea de compás. `-` significa una línea de compás invisible, `||` es una línea de compás doblemente fina, `|!:` es una repetición izquierda, `:|!|:` es una repetición izquierda-derecha.  Un estilo especial es `==`, que representa una barra final.  Este compás no suele incluir un número de compás, ya que es el último de la pieza/movimiento.

{% include verovio.html
	source="bar2"
	scale="55"
	humdrum-min-height="340px"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="bar2">
**kern
*clefG2
=1
1c
=2-
1d
=3||
1e
=4
1f
=5!|:
1g
=6:|!|:
1a
=7:|!
1b
==
*-
</script>


Humdrum puede representar más estilos de barras de compás, pero los tipos anteriores están actualmente soportados en Verovio.


### Compases de anacrusa ###

Normalmente, la barra de compás inicial debe ser etiquetada en la codificación de Humdrum aunque no se imprima.  Se debe usar `=1` o `=1-` al comienzo del primer compás (con `-` significando una línea de compás invisible), pero la barra de compás inicial se suprimirá automáticamente si es una barra de compás normal.  Etiquetar el primer compás es necesario si necesitas extraerlo por número de compás con una herramienta como [myank](/filtro/myank).

Los compases de anacrusa no tienen una barra de compás al comienzo.  Si un compás no coincide con la duración del compás al inicio de la música y los datos no comienzan con una barra de compás, se interpretará automáticamente como un compás de anacrusa y se le asignará automáticamente 0 como número de compás para utilizarlo con el filtro `myank`.

Aquí hay un ejemplo de música con un compás de anacrusa, y un final típico que resuelve la duración del compás de anacrusa:

{% include verovio.html
	humdrum-min-height="275px"
	source="bar3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="bar3">
**kern
*clefG2
4G
=1
4c
4c
4c
4e
=2
4g
4e
4e
==
*-
</script>
