---
title: Trémolos
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-tremolos
keywords: humdrum tremolo
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar los trémolos en las columnas de **kern.
sidebar: main_sidebar
permalink: /humdrum/tremolos/index-ES.html
---

Los trémolos se representan en `**kern` codificando las notas individuales del trémolo dentro de un grupo barrado, y añadiendo después una interpretación tándem `*tremolo` antes de las notas del barrado que deben convertirse en un trémolo.

{% include verovio.html
	source="tremolo"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo">
**kern
*M3/4
=1
16eLL
16e
16e
16eJJ
*tremolo
16eLL
16e
16e
16eJJ
16fLL
16f
16e
16eJJ
=2
8fL
8f
8f
8f
8f
8fJ
*Xtremolo
=
*-
</script>

Utiliza `*Xtremolo` para desactivar la conversión de trémolo de las notas barradas:

{% include verovio.html
	source="tremolooff"
	humdrum-min-height="340px"
	scale="75"
%}
<script type="application/json" id="tremolooff">
**kern
*M3/4
16eLL
16e
16e
16eJJ
*tremolo
16eLL
16e
16e
16eJJ
*Xtremolo
16fLL
16f
16e
16eJJ
=
*-
</script>



Cuando el "trémolo" está activo, sólo se convertirán en trémolos los grupos barrados que puedan convertirse en trémolos.  Los demás patrones de notas barradas no se verán afectados.


{% include verovio.html
	source="tremolo3"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo3">
**kern
*M3/4
*tremolo
16eLL
16e
16e
16eJJ
16eLL
16f
16g
16fJJ
32fLL
32f
32f
32f
32e
32e
32e
32eJJ
=
*-
</script>


Los trémolos también funcionan con las notas de acordes barradas


{% include verovio.html
	source="tremolo4"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo4">
**kern
*M3/4
16e 16g 16bLL
16e 16g 16b
16e 16g 16b
16e 16g 16bJJ
*tremolo
16e 16gLL
16e 16g
16e 16g
16e 16gJJ
16e 16g 16bLL
16e 16g 16b
16e 16g 16b
16e 16g 16bJJ
=
*-
</script>

## Trémolos de dos noas ##

La interpretación del `*tremolo` también puede reducir las notas alternas a trémolos:

{% include verovio.html
	source="tremolo5"
	humdrum-min-height="580px"
	scale="75"
%}
<script type="application/json" id="tremolo5">
**kern
*M3/4
=
16eLL
16g
16e
16gJJ
*tremolo
16eLL
16g
16e
16g
16e
16g
16e
16gJJ
=
16eLL
16g
16e
16g
16e
16g
16e
16g
16e
16g
16e
16gJJ
=
*-
</script>


Los trémolos de dos notas también funcionan con los acordes:

{% include verovio.html
	source="tremolo6"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo6">
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>



## Desactivación de los trémolos ##

Los trémolos pueden desactivarse de la representación de la notación utilizando el filtro [shed](/filter/shed):


{% include verovio.html
	source="remove1"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="remove1">
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>

{% include verovio.html
	source="remove2"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="remove2">
!!!filter: shed -e 's/^X?tremolo$//I'
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>


## Filtro tremolo ##

El filtro tremolo puede utilizarse para añadir notas de trémolo a una partitura de Humdrum que no tenga trémolos expandidos.  Para expandir una sola nota en un trémolo, añade la duración del trémolo rodeada de marcadores `@` después de la(s) nota(s):

{% include verovio.html
	source="tremolo1"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo1">
!!!filter: tremolo
**kern
*clefG2
*M4/4
=1
1c@16@
=2
2d@8@
2e@32@
=
*-
</script>

Las partituras no deben almacenarse en formato de trémolo comprimido, ya que la codificación `@` sólo está pensada para añadir trémolos a la partitura utilizando el filtro de trémolo.  Este es el resultado de la compilación del filtro:
s
{% include verovio.html
	source="tremolo1b"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo1b">
!!!Xfilter: tremolo
**kern
*clefG2
*M4/4
=1
*tremolo
16cLL
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16cJJ
=2
8dL
8d
8d
8dJ
32eLLL
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32eJJJ
*Xtremolo
=
*-
</script>


Los trémolos de dos notas se codifican de forma similar.  Coloca la duración del trémolo sólo en la primera nota de un par de dos notas, rodeada de dos caracteres `@@ en lugar de uno.  Cada nota del par debe poseer la mitad de la duración total del trémolo. 

{% include verovio.html
	source="tremolo2"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo2">
!!!filter: tremolo
**kern
*clefG2
*M4/4
=1
2c@@16@@
2d
=2
4d@@8@@L
4eJ
4e@@32@@L
4fJ
=
*-
</script>



El resultado de la compilación del filtro:

{% include verovio.html
	source="tremolo2b"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo2b">
!!!Xfilter: tremolo
**kern
*clefG2
*M4/4
=1
*tremolo
16cLL
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16dJJ
=2
8dL
8e
8d
8eJ
32eLLL
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32fJJJ
*Xtremolo
=
*-
</script>


