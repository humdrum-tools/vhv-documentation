---
title: Filtro chooser
lang: en es
ref: filters-chooser
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 15 Sep 2019
translation_date: 7 Aug 2021
last_updated: 15 Sep 2019
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/chooser/index-ES.html
---

El filtro `chooser` puede utilizarse para extraer o reordenar los segmentos de datos de Humdrum.

Este es un ejemplo de varios movimientos almacenados en segmentos de datos separados.  El segundo se muestra a la derecha ya que el segundo segmento de datos está seleccionado por el filtro.

{% include verovio.html
	source="chooser2"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="800px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="chooser2">
!!!!filter: chooser -s 2
**kern
*M4/4
=1
1c
==
*-
**kern
*M4/4
=1
1d
==
*-
**kern
*M4/4
=1
1e
==
*-
**kern
*M4/4
=1
1f
==
*-
**kern
*M4/4
=1
1g
==
*-
**kern
*M4/4
=1
1a
==
*-
**kern
*M4/4
=1
1b
==
*-
</script>

Pruebe a cambiar `!!!!filter: chooser -s 2` por otro número de segmento, como el quinto segmento que muestra una nota redonda Sol.



### Elección de varios segmentos ###

El filtro `chooser` también puede reordenar el orden de los segmentos en los datos de Humdrum.   He aquí un ejemplo de inversión del orden de los segmentos y de extracción del segundo segmento de los datos reordenados.  Dado que el último segmento contenía un SI,
que se convierte en el primer segmento después de invertir los segmentos, se muestra un tono LA como resultado del filtro.
s

{% include verovio.html
	source="chooser3"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="800px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="chooser3">
!!!!filter: chooser -s $-1
!!!!filter: chooser -s 2
**kern
*M4/4
=1
1c
==
*-
**kern
*M4/4
=1
1d
==
*-
**kern
*M4/4
=1
1e
==
*-
**kern
*M4/4
=1
1f
==
*-
**kern
*M4/4
=1
1g
==
*-
**kern
*M4/4
=1
1a
==
*-
**kern
*M4/4
=1
1b
==
*-
</script>

El símbolo `$` (o, de forma equivalente, `%`) se utiliza para representar el último segmento de los datos.  Así, `$-1` significa extraer desde el último segmento hasta el primero, es decir, extraer los segmentos en orden inverso.  Se puede utilizar una coma para separar segmentos no contiguos, como `!!!!filter: chooser 1,3,5,2-4`.  Esto se expandirá al orden de los segmentos `1,3,5,2,3,4`.


