---
title: Codificación de ligaduras de expresión en Humdrum
lang: en es
ref: humdrum-getting_started-slurs
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial slurs
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 7 Dec 2019
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Cómo codificar las ligaduras de expresión en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/slurs/index-ES.html
---

<!--{% include humdrum/slurs.txt %}-->
## Slurs ##

Las ligaduras de expresión se indican añadiendo `(` a un token para el inicio de la ligadura, y `)` para el final de la misma.

{% include verovio.html
	humdrum-min-height="275px"
	source="slur1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slur1">
**kern
*M4/4
=1
(4c
4d
4e
4f
=2
4g
4f
4e
4c)
==
*-
</script>

### Ligaduras anidadas ###

Las ligaduras pueden anidarse abriendo otra ligadura mientras otra está activa.  La primera ligadura que se cierre afectará a la ligadura que se abra más cerca de ella.

{% include verovio.html
	humdrum-min-height="300px"
	source="slur2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slur2">
**kern
*M4/4
=1
(4c
(>4d
(4e
(>4f
=2
4g)
4f)
4e)
4c)
==
*-
!!!RDF**kern: > = above
</script>

Obsérvese el carácter RDF de dirección que puede utilizarse para forzar la dirección de una ligadura.

### Cruce de ligaduras ###

Las ligaduras pueden cruzarse entre sí anteponiendo un signo de ampersand (`&`) delante de un marcador de ligadura que se cruce con otra.  Si hay más de una ligadura que se cruza a la vez, se pueden añadir caracteres `&` adicionales al prefijo de la ligadura.

{% include verovio.html
	humdrum-min-height="310px"
	source="slur3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slur3">
**kern
*M4/4
=1
(4c
&(>4d
4e)
(4f&)
=2
&(4g
&&(4f
4e)
4c&)
=3
1d&&)
==
*-
!!!RDF**kern: > = above
</script>


<!-- End include -->

## Orientación de la ligadura ##

Hay dos maneras de controlar la colocación de las ligaduras en el pentagrama.  Cuando sea necesario colocar una ligadura en una posición arbitraria, utilice uno de los dos sistemas siguientes.

### Mediante parámetros de disposición ###


{% include verovio.html
	humdrum-min-height="315px"
	source="slurlayoutpos"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurlayoutpos">
**kern
*M4/4
=1
(4c
4d)
!LO:S:a
(4e
4f)
=2
(4cc
4dd)
!LO:S:b
(4ee
4ff)
==
*-
</script>

El prefijo de disposición `!LO:S:` indica que el parámetro de disposición se aplica a la ligadura en el siguiente dato de la columna.  Para forzar la ligadura por encima del pentagrama, añade el parámetro `a`, que es la abreviatura de `a=true`.  Para forzar la ligadura por debajo del pentagrama, añade el parámetro `b`.

### Mediante registros RDF ###

Cuando las orientaciones de las ligaduras deben ajustarse con frecuencia en una partitura, una forma más compacta de codificarlas es utilizar un registro RDF:

{% include verovio.html
	humdrum-min-height="325px"
	source="slurrdf"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurrdf">
**kern
*M4/4
=1
(4c
4d)
(>4e
4f)
=2
(4cc
4dd)
(<4ee
4ff)
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

En el ejemplo anterior, el carácter `<` se define como una propiedad en la ligadura para forzarla por debajo del pentagrama, y `>` se utiliza para forzar la ligadura por encima del pentagrama.  Estos caracteres deben seguir inmediatamente al carácter `(` que representa el inicio de la ligadura.  Otras posiciones en el token harán que la ligadura o el barrado se orienten hacia arriba o hacia abajo, y la colocación de los significantes arriba/abajo después de una nota la moverá al siguiente pentagrama por encima o por debajo del actual.

### Ligaduras en los acordes ###

Cuando un acorde posee dos ligaduras, las dos ligaduras se desplazarán a lados opuestos del acorde automáticamente:

{% include verovio.html
	humdrum-min-height="325px"
	source="slurchord"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurchord">
**kern
*M4/4
=1
(2c 2e 2g
2d 2f 2a)
=2
((2c 2e 2g
2d 2f 2a))
=3
(2c 2e (2g
2d) 2f 2a)
=4
2c 2e 2g((
2d 2f 2a))
==
*-
</script>

La posición de la ligadura en el acorde no es importante: la ligadura está unida al acorde, no a ninguna nota individual del mismo.


## Ligaduras de puntos y rayas ##

Los parámetros de disposición pueden anteponerse al token de inicio de una ligadura para mostrar la ligadura como líneas punteadas o discontinuas.


{% include verovio.html
	humdrum-min-height="315px"
	source="slurdashdot"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurdashdot">
**kern
*M4/4
=1
!LO:S:dash
(4c
4d
4e
4f)
=2
!LO:S:dot
(4c
4d
4e
4f)
==
*-
</script>

El prefijo de diseño `!LO:S:` significa que el parámetro de disposición se aplica a una ligadura en el siguiente token de datos.   Para mostrar la ligadura como una línea discontinua, añade el parámetro `dash`, que equivale a `dash=true`. Para mostrar la ligadura como una línea punteada, añade el parámetro `dot`.

### Múltiples ligaduras ###

Las ligaduras múltiples sobre notas o acordes pueden ser abordadas individualmente dentro del parámetro de disposición añadiendo el parámetro `n` al número de la ligadura.  Por ejemplo, si hay dos ligaduras, se puede referenciar la primera añadiendo `n=1` al parámetro de disposición, y `n=2` para la segunda.

{% include verovio.html
	humdrum-min-height="415px"
	source="multiplestyle"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multiplestyle">
**kern
*M4/4
=1
!LO:S:dash
((2c 2e
2f 2cc))
=2
!LO:S:dash:n=1
((2c 2e
2f 2cc))
=3
!LO:S:dash:n=2
((2c 2e
2f 2cc))
=4
!LO:S:dash:n=1
!LO:S:dot:n=2
((2c 2e
2f 2cc))
==
*-
</script>


## Coloreado de ligaduras ##

Las ligaduras se pueden colorear dando un color SVG como parámetro de diseño `color`:

{% include verovio.html
	humdrum-min-height="450px"
	source="slurcolor"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurcolor">
**kern
*M4/4
=1
!LO:S:color=hotpink
(4c
4d
4e
4f)
=2
!LO:S:dot
!LO:S:a
!LO:S:color=#00ff00
(4c
4d
4e
4f)
=2
!LO:S:n=1:dot:color=violet
!LO:S:n=2:dash:color=dodgerblue
((2c 2g
2d 2b))
==
*-
</script>


## Marcas de frase ##

Las marcas de frase son similares a las ligaduras, pero se utilizan para marcar frases analíticas en datos `**kern`.  El estilo de representación por defecto para las frases es un corchete abierto:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrase"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrase">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
</script>


### Estilos de representación de frases ###

Las marcas de frase pueden ser representadas en una variedad de estilos y colores como se ilustra a continuación:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasestyles"
	scale="55"
	pageWidth="1150"
%}
<script type="application/x-humdrum" id="phrasestyles">
**kern
=1
!!LO:TX:b:t=bracket styles
{4c
4d
4e
4f}
=2
!LO:P:brack
{4c
4d
4e
4f}
=3
!LO:P:dot
{4c
4d
4e
4f}
=4
!LO:P:dash
{4c
4d
4e
4f}
=5
!LO:P:open
{4c
4d
4e
4f}
=6||
!!LO:TX:b:t=slur styles
!LO:P:slur
{4c
4d
4e
4f}
=7
!LO:P:slur:dot
{4c
4d
4e
4f}
=8
!LO:P:slur:dash
{4c
4d
4e
4f}
=9||
!!LO:TX:b:t=coloring
!LO:P:slur:dash:color=dodgerblue
{4c
!LO:P:dot:color=red
{4d
4e}
4f}
=10
!LO:P:dash:color=dodgerblue
{4c
!LO:P:dot:color=red
&{4d
4e}
4f&}
=11||
!!LO:TX:b:t=invisible
{y4c
4d
4e
4f}
=12
!LO:P:none
{4c
4d
4e
4f}
==
*-
</script>


### Estilo de representación por defecto para las marcas de frases ###

Se puede utilizar un registro RDF para establecer el estilo de representación por defecto de las marcas de frase.


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasedefault"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrasedefault">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
!!!RDF**kern: { = phrase, brack color=orange
</script>

Varios estilos de representación:

| estilo | resultado |
|-------|--------|
| `brack` | corchetes |
| `dot` | corchetes punteados |
| `dash` | corchetes con líneas discontinuas |
| `none` | sin corchete |
| `open` | corchete abierto (por derecto) |
| `slur` | ligadura |
| `slur dot` | ligadura punteada |
| `slur dash` | ligadura con líneas discontinuas |

Al estilo de frase por defecto también se le puede dar un color como en el ejemplo anterior.


He aquí un ejemplo de supresión de las marcas de frase por defecto, pero dando un estilo local a la última frase:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasenone"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrasenone">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
!LO:P:dash:color=violet
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
!!!RDF**kern: { = phrase, none
</script>


## Cruce de ligaduras entre pentagramas ##

Las ligaduras que cruzan pentagramas pentagrama (en particular para la música de piano), pueden crearse
utilizando un registro RDF como en el siguiente ejemplo:


{% include verovio.html
	humdrum-min-height="275px"
	source="slurlinked"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="slurlinked">
**kern	**kern
*clefF4	*clefG2
*M4/4	*M4/4
=1	=1
*^	*^
N(4F	1FF	4cc/	2f\
4c	.	4ee/	.
2A\	.	2gg	4f
.	.	.	4gN)
*	*	*v	*v
*v	*v	*
=	=
*-	*-
!!!RDF**kern: N = linked
</script>

El registro RDF `N = linked` se utiliza para crear el enlace entre los dos extremos de la ligadura en los datos.  El significante de enlace debe ir inmediatamente delante de los significantes de enlace en los datos.


