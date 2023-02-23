---
title: filtro sic
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: filters-sic
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/sic/index-ES.html
---
El filtro sic se utiliza para controlar la visualización de errores y correcciones simples para las ediciones de origen.  Tanto el contenido musical original como el contenido corregido están codificados en la partitura, y el filtro sic controla qué versión se muestra.

Aquí hay un ejemplo de codificación SIC, donde la notación original tiene un Fa negra, pero se determinó que un Sol negra es correcto:

{% include verovio.html
	source="sic1"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic1">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>

Las líneas:

```
!LO:SIC:s=4g
4f
```
significa que la nota original en la edición de origen es una negra F4, pero se ha decidido que la nota correcta debería haber sido una negra G4.  El parámetro `s` significa el contenido de "sustitución" que debería reemplazar el contenido de la nota siguiente en la partitura.

Alternativamente, se puede mostrar la corrección, y el parámetro SIC puede almacenar lo que mostraba la notación original:

{% include verovio.html
	source="sic2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic2">
**kern
*M4/4
=1
4c
4e
!LO:SIC:o=4f
4g
4cc
=
*-
</script>

En este caso el parámetro `o` significa el contenido "original" que fue reemplazado por el contenido correcto en la partitura.


## Cambio entre el contenido original y el corregido ##

El filtro sic puede cambiar entre el contenido original y el de la sustitución.  Para forzar que se muestren las correcciones, utiliza `!!!filtro: sic -s`:

{% include verovio.html
	source="sic3"
	scale="50"
	humdrum-min-width="180"
	humdrum-min-height="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic3">
!!!filter: sic -s
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>

En este ejemplo, la partitura codifica el contenido original, pero el filtro sic lo cambiará por el contenido de sustitución, por lo que en lugar de mostrarse el `4f` en la notación, se utiliza el `4g`.

Del mismo modo, si se quiere codificar la corrección en la partitura, el parámetro SIC puede almacenar el contenido original, y `!!!filtro: sic -o` se puede utilizar para mostrar el contenido original que fue corregido:

{% include verovio.html
	source="sic4"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic4">
!!!filter: sic -o
**kern
*M4/4
=1
4c
4e
!LO:SIC:o=4f
4g
4cc
=
*-
</script>

## Displaying sic warnings in VHV ##

Si quiere marcar visualmente que las notas/silencios tienen parámetros de diseño SIC adjuntos, añada el parámetro `v` (que significa "verboso"):

{% include verovio.html
	source="sicv"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicv">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g:v
4f
4cc
=
*-
</script>

En el editor VHV, la "S" verde se convierte en un icono de triángulo verde:


{% include image.html
	file="sic-marker.png"
	alt="sic marker"
	max-width="40%"
	caption="Verbose sic marker dipslay in VHV editor"
%}

Tanto la visualización original como la de sustitución mostrarán un triángulo verde cuando la visualización verbosa esté activa (depende de ti saber qué forma se está mostrando, por ejemplo forzando una vista concreta con el filtro sic).

Si quieres forzar la visualización del marcador sic en la partitura gráfica, utilice ``filtro: sic -v`':


{% include verovio.html
	source="sicv2"
	scale="50"
	humdrum-min-width="180"
	humdrum-min-height="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicv2">
!!!filter: sic -v
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>

En el futuro, se podría añadir otro parámetro (como `v=text`) para que el texto verde muestre el texto original/sustituido sobre la nota en lugar de una S mayúscula. Así, el ejemplo anterior mostraría `4g` como texto en lugar de `S`.

## SIC para articulaciones ##

El sistema SIC está pensado para correcciones sencillas de notas/silencios.  También puede utilizarse para indicar problemas evidentes en las articulaciones:


{% include verovio.html
	source="sicstaccato"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicstaccato">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4g'
4cc
=
*-
</script>

En este ejemplo, la partitura original tiene un staccato en el Sol, pero se determinó que era un error.  Tenga en cuenta que esto es diferente de los staccatos implícitos, que se codificarían con marcadores `y` después de los staccatos:


{% include verovio.html
	source="staccato"
	scale="50"
	humdrum-min-width="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="staccato">
**kern
*M4/4
=1
4c'
4e'
!LO:TX:b:i:t=simile
4g'y
4cc'y
=
*-
</script>



## SIC para acordes ##
El filtro sic sólo sustituye tokens enteros, por lo que si hay que arreglar una sola nota de un acorde, habrá que añadir todo el acorde al parámetro SIC `s` o `o`:

{% include verovio.html
	source="chord"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="160"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="chord">
**kern
*M4/4
=1
4c 4e 4g
!LO:SIC:s=4c 4f 4a
4c 4f 4g
=
*-
</script>

Así, `!!!filter: sic -s` producirá:

{% include verovio.html
	source="chord2"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="175"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="chord2">
!!!filter: sic -s
**kern
*M4/4
=1
4c 4e 4g
!LO:SIC:s=4c 4f 4a
4c 4f 4g
=
*-
</script>


## SIC for ties ##

He aquí un ejemplo de utilización del sistema SIC para codificar una ligadura de prolongación que falta.

{% include verovio.html
	source="tie"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="300"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tie">
**kern
*M4/4
=1
4c
4d
4e
!LO:SIC:s=[4f
4f
=2
!LO:SIC:s=4f]
4f
4e
4d
4c
=
*-
</script>

Entonces, `!!!filter: sic -s` producirá:


{% include verovio.html
	source="tie2"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="315"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tie2">
!!!filter: sic -s
**kern
*M4/4
=1
4c
4d
4e
!LO:SIC:s=[4f
4f
=2
!LO:SIC:s=4f]
4f
4e
4d
4c
=
*-
</script>



## SIC para ligaduras de expresión ##

He aquí un ejemplo de utilización del sistema SIC para codificar una ligadura de expresión.

{% include verovio.html
	source="slur"
	scale="50"
	humdrum-min-width="220"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="slur">
**kern
*M4/4
=1
!LO:SIC:s=(4c
4c
4d
4e
!LO:SIC:s=4f)
4f
=
*-
</script>

De forma que `!!!filter: sic -s` produciirá:

{% include verovio.html
	source="slur2"
	scale="50"
	humdrum-min-width="220"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="slur2">
!!!filter: sic -s
**kern
*M4/4
=1
!LO:SIC:s=(4c
4c
4d
4e
!LO:SIC:s=4f)
4f
=
*-
</script>





