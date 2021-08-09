---
title: filtro imitation
lang: en es
ref: filters-imitation
author: "Craig Sapp"
translator: David Rizo
creation_date: 18 Jun 2017
translation_date: 8 Aug 2021
last_updated: 18 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "El filtro imitation identifica la repetición melódica modal entre voces."
permalink: /filter/imitation/index-ES.html
---
La herramienta de imitación identifica patrones de intervalos repetidos entre las voces.  El siguiente ejemplo muestra los resultados de la herramienta para las dos voces iniciales de la primera fuga del Clave bien temperado de J.S. Bach, Libro I (BWV 846).

{% include verovio.html
	source="wtc1f01m1t4"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="wtc1f01m1t4">
!!!filter: imitation
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Prueba a cambiar los tonos en la música textual de la izquierda para ver cómo cambian las coincidencias.


## Resumen ##
Debajo de la primera nota de cada par de imitaciones, una cadena de texto ofrece cuatro datos sobre la imitación.  Los cuatro campos están separados por dos puntos, y cada valor va precedido de una letra:

prefijo | significado del parámetro
=======|=================
n      | Un ID de enumeración único para cada par de imitación dentro de la puntuación, empezando por 1.
c      | El *contador* de cada nota cen ada uno de los emparejamientos de imitación. 
d      | La *distancia* (duración) entre la primera nota de cada par de imitaciones.  Un valor positivo significa que la imitación ocurre después de la secuencia actual, mientras que un valor negativo significa que la otra secuencia de imitación viene antes de la secuencia actual. 
i      | El *intervalo* de imitación en tonos diatónicos.  Los valores positivos significan que la imitación en la otra ubicación es más alta en tono que la secuencia actual, mientras que un valor negativo significa que la secuencia emparejada está en un tono más bajo. 

Así, el texto bajo la primera nota del ejemplo anterior (`n1:c14:d6:i5`) significa que se trata del primer par, donde hay 14 notas compartidas (13 intervalos), la imitación está en la quinta, y la distancia entre los inicios de la secuencia es de 6 negras.

## Supresión de información ##

Existen varias opciones para modificar la visualización de la información de coincidencia.  Para suprimir completamente la información de coincidencia, utilice la opción `-q` (que significa "silenciosa"):

{% include verovio.html
	source="quiet"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="quiet">
!!!filter: imitation -q
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Las coincidencias siguen resaltadas, pero no se añade información textual a la puntuación.  También puedes eliminar selectivamente los campos `n`, `c`, `d` o `i` añadiendo la opción `-N`, `-C`, `-D` o `-I` respectivamente.  Aquí hay un ejemplo de eliminación de los campos "count" y "distance" al mismo tiempo:
s

{% include verovio.html
	source="nocd"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nocd">
!!!filter: imitation -CD
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Se puede suprimir la información de la segunda secuencia de la coincidencia utilizando la opción `-f`, lo que significa dar sólo la información de la "primera" secuencia del par:
s

{% include verovio.html
	source="first"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="first">
!!!filter: imitation -f
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Las opciones `--NN`, `--CC`, `--DD` y `--II` pueden suprimir selectivamente los campos de la segunda coincidencia.  Este es un ejemplo que muestra sólo el campo `n` en el segundo par de una coincidencia:

{% include verovio.html
	source="nonly"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nonly">
!!!filter: imitation --CC --DD --II
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

La opción `-2` es un atajo para `--CC --DD --II`:


{% include verovio.html
	source="nonly2"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nonly2">
!!!filter: imitation -2
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


## Adición de información ##
La opción `-m` puede utilizarse para añadir números de compás a la información de coincidencia, y `-b` puede añadir la información de tiempo.  La información del tiempo está en unidades de negra (independientemente del compás), con el primer tiempo de un compás etiquetado como tiempo "1".

{% include verovio.html
	source="measure"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="measure">
!!!filter: imitation -mb
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>
La `-l` (L minúscula), se puede utilizar para incluir la longitud de la secuencia coincidente:
s
{% include verovio.html
	source="length"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="length">
!!!filter: imitation -l
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

La longitud va precedida de la letra `L` en la cadena de información.  En este caso, la longitud de ambas coincidencias es de 5.75 negras.



## Umbral de recuento de notas ##
La opción `-t` se utiliza para establecer un umbral de número de notas que deben coincidir.  El número de notas por defecto es 7. En la música del ejemplo, hay 14 notas que coinciden entre las dos entradas fugadas, por lo que si el umbral se establece en 15, este par no se identificará:

{% include verovio.html
	source="threshold"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="threshold">
!!!filter: imitation -t 15
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Pero si se fija el umbral en 14 se obtendrá una coincidencia:


{% include verovio.html
	source="threshold14"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="threshold14">
!!!filter: imitation -t 14
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


## Distancia máxima entre la imitación ##
La opción `-d` puede utilizarse para limitar la distancia (duración) entre las coincidencias.  Esto es útil para resaltar las entradas imitativas y minimizar el ruido de las coincidencias.  Por defecto, se permite cualquier duración entre coincidencias.  Para limitar la distancia de búsqueda entre coincidencias, especifique la duración máxima entre pares en unidades de negra.  A continuación se muestra un ejemplo en el que se limita la distancia de coincidencia a 4 negras.  Como la distancia entre las entradas fugadas es de 6 negras, no se identifica ninguna coincidencia:


{% include verovio.html
	source="distance4"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="distance4">
!!!filter: imitation -d 4
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Si se aumenta la distancia mínima a 6 negras o más, se captará la imitación:

{% include verovio.html
	source="distance6"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="distance6">
!!!filter: imitation -d 6
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

## Imitación por altura pero no por ritmo ##
La opción `-p` sólo tendrá en cuenta las alturas de las notas al buscar coincidencias, ignorando sus duraciones.  Este es un ejemplo de coincidencia entre dos secuencias que tienen las mismas alturas en secuencia, pero los ritmos son diferentes:


{% include verovio.html
	source="pitch"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="pitch">
!!!filter: imitation -p
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	1r
4d	.
4e	.
4f	.
=2	=2
4g	8.cL
.	16dJ
4a	8.eL
.	16fJ
4b	8gL
.	8a
4cc	8b
.	8ccJ
=	=
*-	*-
</script>


## Concordancia de inversiones ##
La opción `-v` puede utilizarse para buscar coincidencias de inversiones.  Este es un ejemplo en el que una escala ascendente y otra descendente coinciden entre sí:

{% include verovio.html
	source="inversion"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="inversion">
!!!filter: imitation -v
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	2r
4d	.
4e	4cc
4f	4b
=2	=2
4g	4a
4a	4g
4b	4f
4cc	4e
2r	4d
.	4c
=	=
*-	*-
</script>
Observa que el número de enumeración lleva el prefijo `v` para indicar que la relación de imitación en una inversión.  El valor del intervalo indica el intervalo entre el primer par de notas de las dos secuencias.

Si se añade la opción `-a` a la opción `-v`, se buscarán tanto las coincidencias regulares como las coincidencias por inversión al mismo tiempo.  He aquí un ejemplo:

{% include verovio.html
	source="add"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="add">
!!!filter: imitation -av
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	8cL
.	8eJ
4d	8gL
.	8ccJ
4e	8bL
.	8ddJ
4f	4cc
=2	=2
4g	4b
4a	4a
4b	4g
4cc	4f
=3	=3
8cL	4e
8eJ	.
8gL	4d
8ccJ	.
8bL	4B
8ddJ	.
4cc	4c
=	=
*-	*-
</script>

Cada tipo de búsqueda tendrá un color diferente (pero sólo se puede mostrar un color cuando los tipos de coincidencia se superponen).

## Seleccionar o evitar el movimiento paralelo ##
La opción '-z' puede utilizarse para seleccionar sólo las imitaciones que se inician al mismo tiempo. Es un alias de `-d 0`:

{% include verovio.html
	source="parallel"
	spacingStaff="8"
	scale="35"
	pageWidth="1450"
	tabsize="10"
%}
<script type="application/x-humdrum" id="parallel">
!!!filter: imitation -z
**kern	**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M4/2	*M4/2	*M4/2	*M4/2
=34	=34	=34	=34
4c	4f	0r	1r
8BL	4e	.	.
8cJ	.	.	.
4d	2.d	.	.
4c	.	.	.
4B	.	.	2r
4e	4c	.	.
2d	2B	.	[2g
=35	=35	=35	=35
2c	4e	4r	4g]
.	2c	2e	4a
2r	.	.	4g
.	4d	4f	8fL
.	.	.	8gJ
1r	4c	4e	4a
.	8BL	8dL	4g
.	8cJ	8eJ	.
.	4d	4f	[2f
.	4c	4e	.
=36	=36	=36	=36
1r	4B-X	4d	4f]
.	4G	4d	4g
.	2A	2c#X	2e
2r	2A	4d	2d
.	.	4d	.
2A	2d	[2f	4r
.	.	.	4a
=37	=37	=37	=37
2D	2d	2f]	2b-X
2G	2c	2e	2g
4F	4c	4f	4a
4G	4c	4e	4g
4G	4c	4.e	4g
4c	4e	.	4a
.	.	8f	.
=	=	=	=
*-	*-	*-	*-
</script>

La opción '-Z' hará lo contrario: eliminará cualquier par de imitación que comience al mismo tiempo:
s
{% include verovio.html
	source="noparallel"
	spacingStaff="8"
	scale="35"
	pageWidth="1450"
	tabsize="10"
%}
<script type="application/x-humdrum" id="noparallel">
!!!filter: imitation -Z
**kern	**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M4/2	*M4/2	*M4/2	*M4/2
=34	=34	=34	=34
4c	4f	0r	1r
8BL	4e	.	.
8cJ	.	.	.
4d	2.d	.	.
4c	.	.	.
4B	.	.	2r
4e	4c	.	.
2d	2B	.	[2g
=35	=35	=35	=35
2c	4e	4r	4g]
.	2c	2e	4a
2r	.	.	4g
.	4d	4f	8fL
.	.	.	8gJ
1r	4c	4e	4a
.	8BL	8dL	4g
.	8cJ	8eJ	.
.	4d	4f	[2f
.	4c	4e	.
=36	=36	=36	=36
1r	4B-X	4d	4f]
.	4G	4d	4g
.	2A	2c#X	2e
2r	2A	4d	2d
.	.	4d	.
2A	2d	[2f	4r
.	.	.	4a
=37	=37	=37	=37
2D	2d	2f]	2b-X
2G	2c	2e	2g
4F	4c	4f	4a
4G	4c	4e	4g
4G	4c	4.e	4g
4c	4e	.	4a
.	.	8f	.
=	=	=	=
*-	*-	*-	*-
</script>



