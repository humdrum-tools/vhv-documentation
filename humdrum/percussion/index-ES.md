---
title: Percusión
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-tuplet_styling
keywords: humdrum percussion
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Métodos de codificación de las partes de percusión.
sidebar: main_sidebar
permalink: /humdrum/percussion/index-ES.html
---

Las partes de percusión se codifican en las columnas `**kern`, utilizando una clave de percusión y marcadores para indicar las notas no afinadas o semiafinadas, así como el control de los parámetros de interpretación o disposición de las formas de las cabezas de las notas.

## Clave de percusión ##

Utiliza `*clefX` para una clave de percusión, con `X` que significa sin tono.

{% include verovio.html
	source="xclef"
	pageWidth="1450"
	scale="60"
	humdrum-height="105"
	humdrum-min-height="105"
%}
<script type="application/json" id="xclef">
**kern
*clefX
*M4/4
1bR
*-
</script>

Si se da un número después de "X", la clave se centrará en esa línea.

{% include verovio.html
	source="xclef5"
	pageWidth="1450"
	scale="60"
	humdrum-height="105"
	humdrum-min-height="105"
%}
<script type="application/json" id="xclef5">
**kern
*clefX5
*M4/4
1bR
*-
</script>





## Líneas de pentagrama ##

Para fijar el número de líneas de un pentagrama, añade la interpretación `*stria` al principio de la columna antes de cualquier dato (notas/silencios), añadiendo el número de líneas al final de la interpretación. 

{% include verovio.html
	source="stria1"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="stria1">
**kern
*stria1
*clefX
*M4/4
4eR
8eRL
8eRJ
8eR/L
8eR/J
4eR/
*-
</script>


## Notas no afinadas ##

La colocación de las notas en el pentagrama se controla asignando nombres de afinación a las notas, y se colocarán como si estuvieran en un pentagrama de clave de Sol.  Si hay una sola línea en el pentagrama, entonces se trata como la línea inferior de la clave de sol, y las notas colocadas en esta línea tienen la "afinación" de `e`.

Las notas de percusión deben incluir la letra `R` para indicar que no están afinadas.  Esto es importante a efectos de análisis, por lo que las notas de percusión sin la calificación `R` se resaltarán en rojo para indicar un problema:

{% include verovio.html
	source="unpitched"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="unpitched">
**kern
*stria1
*clefX
*M4/4
4e
8eL
8eJ
8eR/L
8eR/J
4eR/
*-
</script>

## Notas parcialmente afinadas ##

Si las notas no están afinadas, pero tampoco totalmente desafinadas, se puede utilizar el marcador `RR` para indicar que una nota está parcialmente afinada.  Esto es útil para instrumentos como los tom-toms o <a target="_blank" href="https://www.youtube.com/watch?v=7otWy6LcaRA">rototoms</a> en los que los tambores están afinados de menor a mayor.  En este caso, se puede utilizar la altura de tono general para el análisis en lugar del tono anotado.


{% include verovio.html
	source="semipitched"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="semipitched">
**kern
*clefX
*M4/4
4eRR
8gRRL
8ffRRJ
8ddRR/L
8dRR/J
4gRR/
*-
</script>

## Formas de cabeza de nota ##

Las formas de las cabezas de nota pueden establecerse mediante parámetros de diseño aplicados a notas individuales, o mediante una interpretación de la forma de la cabeza de nota que afecta a todas las notas que le siguen en la música.  Formas de cabeza de nota disponibles:

| forma   | descripción |
| ------- | ----------- |
| x       | cabeza de nota con forma de "x" |
| plus    | cabeza de nota con forma de signo más |
| dia     | cabeza de nota con forma de diamante |
| slash   | forma de la cabeza de nota de barra de acorde |
| solid   | forma de la cabeza de la nota de las negras y más cortas |
| open    | cabeza de nota con forma de blanca |
| whole   | cabeza de nota con forma de redonda |
| regular | forma de cabeza de nota normals |


### Método del parámetro de disposición ###

Añade un parámetro de diseño de nota inmediatamente antes de la nota con un parámetro "cabeza" ajustado a la forma de la cabeza de la nota:

{% include verovio.html
	source="shape1"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="400"
%}
<script type="application/json" id="shape1">
**kern
*stria1
*clefX
=1
!LO:N:head=x
4eR
!LO:N:head=plus
4eR
!LO:N:head=dia
4eR
!LO:N:head=slash
4eR
!LO:N:head=solid
4eR
!LO:N:head=open
4eR
!LO:N:head=whole
4eR
!LO:N:head=regular
4eR
*-
</script>


### Método de interpretación ###

Si la forma de la cabeza de la nota no cambia a menudo, utiliza la interpretación `*head`:

{% include verovio.html
	source="shape2"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="350"
%}
<script type="application/json" id="shape2">
**kern
*stria3
*clefX
*M4/4
*head:x
4eR/
8gR/L
8bR/J
8bR/L
8eR/J
4gR/
*head:dia
16bRL
16aR
16gR
16fRJ
4eR
*-
</script>

## Silencios ##

Los silencios suelen estar centrados en las líneas del pentagrama:


{% include verovio.html
	source="rest1"
	pageWidth="1450"
	humdrum-max-height="150"
	scale="45"
	humdrum-min-width="350"
%}
<script type="application/json" id="rest1">
**kern	**kern	**kern	**kern	**kern
*stria5	*stria4	*stria3	*stria2	*stria1
*clefX	*clefX	*clefX	*clefX	*clefX
1r	1r	1r	1r	1r
2r	2r	2r	2r	2r
4r	4r	4r	4r	4r
8r	8r	8r	8r	8r
16r	16r	16r	16r	16r
=	=	=	=	=
*-	*-	*-	*-	*-
</script>


Como los silencios no están afinados, no es necesario añadir los marcadores `R` que se necesitan para las notas que no suenan.


Para desplazar los silencios verticalmente, añade el tono de la clave de sol correspondiente a la posición deseada en el pentagrama, donde la línea más baja de la clave de percusión es `e`:


{% include verovio.html
	source="rest2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="245"
%}
<script type="application/json" id="rest2">
**kern
*stria3
*clefX
8r
8rc
8re
8rg
8rb
8rdd
=
*-
</script>


## Transposición ##

A diferencia de las notas afinadas, las no afinadas no serán transpuestas por el filtro de transposición:


{% include verovio.html
	source="transpose1"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose1">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

Aplicando el filtro `transpose -t m3` para transponer la música a una tercera menor:

{% include verovio.html
	source="transpose2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose2">
!!!filter: transpose -t m3
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

Los datos finales transpuestos (compila el filtro con <span class="keypress">alt-c</span>):

{% include verovio.html
	source="transpose3"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose3">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[b-e-a-]
=	=
*head:x	*
8eRL	4e-
16eRL	.
16eRJJ	.
8eRL	8gL
8eR	8f
8eR	8e-
8eRJ	8dJ
4eR	4e-
=	=
*-	*-
</script>

Si necesitas transponer notas no afinadas, elimina temporalmente el marcador `R` y vuelve a añadirlo después de transponer la música.  Utiliza el filtro shed para convertir `R` en un significante no utilizado, como `Z`, y volver a añadirlo después de la transposición como método fácil para forzar la transposición de las notas no afinadas. 

{% include verovio.html
	source="transpose4"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="400"
%}
<script type="application/json" id="transpose4">
!!!filter: shed -ke 's/R/Z/g'
!!!filter: transpose -t m3
!!!filter: shed -ke 's/Z/R/g'
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

El filtro `-k -e 's/R/Z/g'` cambia primero todos los caracteres `R` en `Z` en los datos de `**kern` (`-k` significa que sólo se procesan las columnas de `**kern`, y por defecto sólo se procesan los tokens de datos).  A continuación, el filtro `transpose -t m3` transpone todas las notas hacia arriba una tercera menor tanto en las notas afinadas como en las no afinadas previamente.  Y por último, el filtro `shed -k -e 's/Z/R/g'` cambia los caracteres `Z` por `R` de nuevo.  Estos son los datos finales después de la transposición de las notas no afinadas:

{% include verovio.html
	source="transpose5"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose5">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[b-e-a-]
=	=
*head:x	*
8gRL	4e-
16gRL	.
16gRJJ	.
8gRL	8gL
8gR	8f
8gR	8e-
8gRJ	8dJ
4gR	4e-
=	=
*-	*-
</script>


## Consideraciones sobre el análisis ##

Si deseas realizar un análisis rítmico con datos que contengan notas no afinadas, no es necesario hacer nada especial a la música.  Sin embargo, para el análisis de la afinación con herramientas que no conocen el marcador `R`, primero hay que convertir la `R` en `r` para que estas notas aparezcan como silencios en los datos.  Esto se puede hacer fácilmente con el filtro shed:

{% include verovio.html
	source="analysis1"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="analysis1">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>


Añade el filtro `shed -ke 's/R/r/g'` a los datos:

{% include verovio.html
	source="analysis2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="375"
	humdrum-min-width="300"
%}
<script type="application/json" id="analysis2">
!!!filter: shed -ke 's/R/r/g'
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
!!!filter: shed -s1 -e 's/[JLKk]//g'
</script>


Actualmente hay un error en Verovio que hace que la notación no se muestre si hay un barrado de notas que sólo contiene silencios, por lo que hay que añadir el filtro `shed -s1 -e 's/[JLKk]//g'` si se quieren ver los silencios (por lo demás, esto no es una preparación necesaria para la entrada en las herramientas de análisis, y debería arreglarse en Verovio en el futuro).  La opción `-s1` significa aplicar los comandos sed sólo a la primera columna.

Y después de compilar el filtro (con <span class="keypress">alt-c</span>), los datos tienen silencios que originalmente eran notas no afinadas:

{% include verovio.html
	source="analysis3"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="analysis3">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8er	4c
16er	.
16er	.
8er	8eL
8er	8d
8er	8c
8er	8BJ
4er	4c
=	=
*-	*-
</script>


## Códigos de los instrumentos de percusión ##

Los instrumentos de percusión pueden clasificarse como tales con la interpretación `*ICidio` (idiófono).  Instrumentos específicos:

| Código  | Nombre | Nota MIDI # |
| ----- | ---- | ------ |
| `*Ibdrum`  | bombo (kit)     | 35    |
| `*Icasts`  | castañuelas           |       |
| `*Ipiatt`  | platillos             |       |
| `*Isdrum`  | tambor repicador (kit)    | 38    |
| `*Icrshc`  | platillo crash (kit)  | 49/57 |
| `*Igong`   | gong                |       |
| `*Imarac`  | maracas             | 70    |
| `*Iridec`  | platillos ride (kit)   | 51/59 |
| `*Ispshc`  | platillo splash (kit) | 55    |
| `*Itabla`  | tabla               |       |
| `*Itambn`  | pandereta          | 54    |
| `*Itom`    | tambor tom-tom        | 41/43/45/47/48/50 |
| `*Itrngl`  | triángulo            | 81/80 |










