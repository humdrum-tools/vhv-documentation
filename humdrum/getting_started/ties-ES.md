---
title: Codificación de ligaduras de prolongacióm en Humdrum
lang: en es
ref: humdrum-getting_started-ties
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial ties
creation_date: 20 Aug 2017
translation_date: 18 Aug 2021
last_updated: 7 Dec 2019
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Cómo codificar ligaduras de prolongación en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/ties/index-ES.html
---

<!--{% include humdrum/ties.txt %}-->
## Ligaduras de prolongación ##

Las ligaduras se indican adjuntando `[` a la nota inicial de una ligadura, y `]` a la nota final.  Para las notas intermedias de un grupo ligado, el carácter de subrayado `_` indica que una ligadura anterior termina en la nota al mismo tiempo que comienza una ligadura a la nota siguiente.

{% include verovio.html
	humdrum-min-height="300px"
	evenNoteSpacing="1"
	source="tie1"
	scale="55"
	pageWidth="675"
%}
<script type="application/x-humdrum" id="tie1">
**kern
*M2/4
[4c
=1
4c.]
[8d
=2
2d_
=3
4d] [4a
4a_
=4
2a]
==
*-
</script>


<!-- Fin include -->

## Orientación de las ligaduras ##

Hay dos maneras de controlar la colocación de las ligaduras en el pentagrama.  Cuando sea necesario colocar una ligadura en una posición arbitraria, utiliza uno de los dos sistemas siguientes.

### Mediante parámetros de disposicióm ###


{% include verovio.html
	humdrum-min-height="315px"
	source="tielayoutpos"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tielayoutpos">
**kern
*M4/4
=1
[4f
4f]
!LO:T:a
[4f
4f]
=2
[4ff
4ff]
!LO:T:b
[4ff
4ff]
==
*-
</script>

El prefijo de disposición `!LO:T:` indica que el parámetro de disposición se aplica a la ligadura en el siguiente token de datos de la columna.  Para forzar la ligadura por encima del pentagrama, añade el parámetro `a`, que es la abreviatura de `a=true`.  Para forzar la ligadura por debajo del pentagrama, añade el parámetro `b`.

### Mediante registros RDF ###

Cuando las orientaciones de las ligaduras deben ajustarse con frecuencia en una partitura, una forma más compacta de codificarlas es utilizar un registro RDF:

{% include verovio.html
	humdrum-min-height="325px"
	source="tierdf"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tierdf">
**kern
*M4/4
=1
[4f
4f]
[>4f
4f]
=2
[4ff
4ff]
[<4ff
4ff]
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

En el ejemplo anterior, el carácter `<` se define como una propiedad de la ligadura para forzarla por debajo del pentagrama, y `>` se utiliza para mover la ligadura por encima del pentagrama.  Estos caracteres deben seguir inmediatamente al carácter `[` (o '_') que representa el inicio de la ligadura.  Otras posiciones en el token harán que la ligadura o el barrado se orienten hacia arriba o hacia abajo, y la colocación de los significantes arriba/abajo después de una nota la moverá al siguiente pentagrama por encima o por debajo del actual.


### Ligaduras en los acordes ###

Cuando un acorde posee dos o más ligaduras, pueden orientarse por encima o por debajo utilizando cualquiera de los dos métodos descritos anteriormente.  Para controlar la orientación utilizando un comando de disposición, añade `n=1` al parámetro de disposición para modificar sólo la ligadura de la primera nota, `n=2` para la segunda nota, y así sucesivamente.

{% include verovio.html
	humdrum-min-height="425px"
	source="tiechord"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiechord">
**kern
*M4/4
=1
[4f [4a [4c
4f] 4a] 4c]
[>4f [>4a [>4c
4f] 4a] 4c]
=2
!LO:T:n=1:a
!LO:T:n=2:a
!LO:T:n=3:a
[4f [4a [4c
4f] 4a] 4c]
!LO:T:n=1:b
!LO:T:n=2:b
!LO:T:n=3:b
[4f [4a [4c
4f] 4a] 4c]
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


## Ligaduras de puntos y rayas ##

Los parámetros de diseño pueden anteponerse al token de inicio de una ligadura para mostrarla como líneas punteadas o discontinuas.

{% include verovio.html
	humdrum-min-height="325px"
	source="tiedashdot"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiedashdot">
**kern
*M4/4
=1
[4e
4e]
!LO:T:dash
[4e
4e]
=2
[4e
4e]
!LO:T:dot
[4e
4e]
==
*-
</script>

El prefijo de diseño `!LO:T:` significa que el parámetro de diseño se aplica a una ligadura en el siguiente token de datos.  Para mostrar la ligaduraa como una línea discontinua, añade el parámetro `dash` que es equivalente a `dash=true`. Para mostrar la ligadura como una línea punteada, añade el parámetro `dot`.


## Coloreado de ligaduras ##

Las ligaduras se pueden colorear dando un color SVG como parámetro de diseño `color`:

{% include verovio.html
	humdrum-min-height="375px"
	source="tiecolor"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiecolor">
**kern
*M4/4
=1
!LO:T:color=chartreuse
[2f
2f]
=2
!LO:T:dot
!LO:T:a
!LO:T:color=hotpink
[2f
2f]
=2
!LO:T:n=1:dot:color=chartreuse
!LO:T:n=2:dash:color=hotpink
[2c [2g
2c] 2g]
==
*-
</script>

## Notas ligadas disjuntas ##

A veces, las ligaduras conectan dos notas que no son directamente adyacentes.  Esto suele ocurrir en el caso de arpegios escritos.  En estos casos, duplica el significante de ligadura para indicar que la nota final de la ligadura no sigue directamente a la nota inicial de la misma.


{% include verovio.html
	humdrum-min-height="175px"
	source="tiedisjunct"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="tiedisjunct">
**kern
*M4/4
[[16cL
[[16e
[[16g
[16ccJ
2.c]] 2.e]] 2.g]] 2.cc]
=
*-
</script>

Observa que la última semicorchea es adyacente al acorde al que están ligadas todas las notas, por lo que tiene un significante de ligadura regular.


## Notas ligadas entre pentagramas ##

Las ligaduras que cruzan pentagramas (en particular para la música de piano), pueden crearse utilizando un registro RDF como en el siguiente ejemplo:


{% include verovio.html
	humdrum-min-height="250px"
	source="tielinked"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="tielinked">
**kern	**kern
*clefF4	*clefG2
*M4/4	*M4/4
=1	=1
2F	4f
.	N[4B<
2BN]	4g
.	4f
=	=
*-	*-
!!!RDF**kern: N = linked
!!!RDF**kern: < = below
</script>

El registro RDF `N = linked` se utiliza para crear el enlace entre los dos puntos finales de la ligadura en los datos.  El significante del enlace debe ir inmediatamente delante de los significantes de la ligadura en los datos.  Y el vínculo correspondiente puede ser adyacente o disjunto en el otro pentagrama.


