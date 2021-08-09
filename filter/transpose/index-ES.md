---
transpose: filtro transpose
lang: en es
ref: filters-transpose
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 23 Apr 2017
translation_date: 9 Aug 2021
last_updated: 23 Apr 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/transpose/index-ES.html
---
El filtro de transposición puede utilizarse para transponer la música en un intervalo determinado o a una tonalidad específica.


## Transposición por tonalidad ##
He aquí un ejemplo de transposición de una coral a cuatro voces de Sol mayor a La bemol mayor, utilizando la opción `-k` para cambiar la tonalidad:


```
!!!filter: transpose -k a-
```

{% include verovio.html
	source="chorale"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="chorale">
!!!filter: transpose -k a-
**kern	**kern	**kern	**kern
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*G:	*G:	*G:	*G:
*M3/4	*M3/4	*M3/4	*M3/4
4GG	4B	4d	4g
=1	=1	=1	=1
4G	4B	4d	2g
4E	8cL	4e	.
.	8BJ	.	.
4F#	4A	4d	4dd
=2	=2	=2	=2
4G	4G	2d	4.b
4D	4F#	.	.
.	.	.	8a
4E	4G	4B	4g
=3	=3	=3	=3
4C	8cL	8eL	4.g
.	8BJ	8d	.
8BBL	4c	8e	.
8AAJ	.	8f#J	8a
4GG	4d	4g	4b
=4	=4	=4	=4
2D;	2d;	2f#;	2a;
4GG	4d	4g	4b
=5	=5	=5	=5
4FF#	4A	4d	2dd
4GG	4B	4e	.
4AA	4c	4f#	4cc
=6	=6	=6	=6
4BB	4d	2g	4b
4C	4e	.	2a
4D	8dL	4f#	.
.	8cJ	.	.
=7	=7	=7	=7
2GG;	2B;	2d;	2g;
=:|!	=:|!	=:|!	=:|!
4GG	4d	[4g	4b
=8	=8	=8	=8
4GG	4d	8gL]	4b
.	.	8f#J	.
4AA	4c	8eL	4cc
.	.	8f#J	.
4BB	8BL	[4g	4dd
.	8AJ	.	.
=9	=9	=9	=9
4.BB	8BL	8gL]	4.dd
.	8cJ	8aJ	.
.	4d	8gL	.
8AA	.	8f#J	8cc
4GG	4d	4g	4b
=10	=10	=10	=10
2D;	2d;	2f#;	2a;
[4E	4B	4e	4g
=11	=11	=11	=11
4E]	4G	4e	2b
4D	4B	8f#L	.
.	.	8gJ	.
4C	4e	4a	4cc
=12	=12	=12	=12
4.BB	2d	4a	2dd
.	.	4.g	.
8C	.	.	.
4D	4d	.	4cc
.	.	8f#	.
=13	=13	=13	=13
8GGL	2.d	2g	2.b
8AAJ	.	.	.
4BB	.	.	.
4GG	.	4f	.
=14	=14	=14	=14
2C;	2c;	2e;	2g;
4GG	4d	4g	4b
=15	=15	=15	=15
4FF#	8dL	4.a	2dd
.	8cJ	.	.
4GG	4B	.	.
.	.	8g	.
4AA	4c	4f#	4cc
=16	=16	=16	=16
4BB	2d	2g	2b
4GG	.	.	.
4D	8dL	[4f#	4a
.	8cJ	.	.
=17	=17	=17	=17
8EL	4B	8f#L]	4.g
8D	.	8eJ	.
8C	4c	8eL	.
8BB	.	8f#J	8a
8AA	4d	4g	4b
8GGJ	.	.	.
=18	=18	=18	=18
2D;	2d;	2f#;	2a;
[4G	4d	4g	4b
=19	=19	=19	=19
4G]	2d	2a	2dd
4F#	.	.	.
[4E	4e	8gL	4cc
.	.	8f#J	.
=20	=20	=20	=20
8EL]	2e	2g	4b
8DJ	.	.	.
4C	.	.	2a
4D	8dL	4f#	.
.	8cJ	.	.
=21	=21	=21	=21
2GG;	2B;	2d;	2g;
==	==	==	==
*-	*-	*-	*-
</script>

Prueba a cambiar `a-` por `a` en la primera línea del ejemplo para transponer a La mayor.

El filtro transpose es idéntico a la herramienta de línea de comandos de Humdrum Extras [transpose](http://extras.humdrum.org/man/transpose).  Consulta su documentación para ver más ejemplos de cómo utilizar el filtro de transposición.

## Transposición por intervalo musical ##
La opción `-k` requiere una interpretación de tonalidad presente en los datos, como `*C:` para Do mayor, o `*b-:` para Si bemol menor.  Si este no es el caso, aún puede transponer por un intervalo específico usando la opción `-t`.

Transposición hacia abajo de una tercera mayor: `!!!filter: transpose -t -M3`

Transposición hacia abajo de una sexta menor: `!!!filter: transpose -t m6`

Transposición a una sexta menor: `!!!filter: transpose -t m6`

Transposición de una cuarta perfecta: `!!!filter: transpose -t -P4`

Transposición a una quinta disminuida: `!!!filter: transpose -t d5`

Transposición hacia abajo de un unísono aumentado, como por ejemplo de Mi mayor a Mi bemol mayor:s `!!!filter: transpose -t -A1`

Prueba varias transposiciones de intervalos en el siguiente ejemplo, que comienza en la tonalidad de Do mayor (pero no hay indicación de tonalidad, por lo que no se puede utilizar la opción `-k`).

{% include verovio.html
	source="transpose"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="transpose">
!!!filter: transpose -t M2
**kern
4c
4d
4e
8fL
8f#J
4g
4aL
4a-J
4b
4cc
==
*-
</script>

## Transposición por número de intervalo de base-40 ##
La representación de las alturas de nota en Base-40 permite valores enteros para varios intervalos.  Todos estos números de intervalo pueden calcularse a partir de dos datos: una segunda mayor es un 6 en el sistema, y una segunda menor es un 5. Por ejemplo, una quinta perfecta está compuesta por tres segundas mayores y una segunda menor, por lo que el intervalo de base-40 es 3 * 6 + 1 * 5 = 23.  Una octava tiene 5 segundas mayores y 2 segundas menores, lo que se traduce en 5 * 6 + 2 * 5 = 40 (de ahí el nombre del sistema).  Ten en cuenta que un unísono aumentado es la diferencia entre una segunda mayor y una menor, que es 1.

Prueba a transponer el siguiente ejemplo por el intervalo de base-40, que se da como un número entero después de la opción `-b` en el filtro transpose. Ten en cuenta también que el sistema de base-40 está limitado a un rango de doble bemol a doble sostenido, por lo que los intervalos que transponen a/por triple bemol no funcionarán en el sistema.
{% include verovio.html
	source="base40"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="base40">
!!!filter: transpose -b 6
**kern
4c
4d
4e
8fL
8f#J
4g
4aL
4a-J
4b
4cc
==
*-
</script>



## Transposición `**mxhm` ##
Los símbolos de acordes importados de MusicXML se almacenan en una columna "mxhm". Estos símbolos son entendidos por la herramienta de transposición y serán transpuestos junto con cualquier columna `**kern` en los datos.

A continuación se muestra una obra de ejemplo que contiene una columna de datos `**mxhm`.  La tonalidad original es Do mayor, pero la herramienta de transposición está cambiando la tonalidad de la pieza a Re mayor.  Prueba a transponer la música a otras tonalidades cambiando la `d` de la primera línea del cuadro de texto de abajo por otra tónica.

{% include verovio.html
	source="muss"
	scale="40"
	pageWidth="1250"
	tabsize="10"
%}

<script type="application/json" id="muss">
!!!filter: transpose -k d
**kern	**mxhm
*part1	*part1
*staff1	*
*clefG2	*
*k[]	*
*C:	*C:
*M4/4	*
=1-	=1-
2r	.
!!LO:TX:a:t=N.C.
4c	.
4d	.
=2!|:	=2!|:
2e	C major
4e	.
4g	.
=3	=3
2f	G dominant
4f	.
4a	.
=4	=4
4.g	C major
8a	.
4g	.
4f	.
=5	=5
1e	.
=6	=6
4.g	.
8a	.
4g	.
4f	.
=7	=7
2e	.
4e	.
4g	.
=8	=8
2f	D minor
4f	.
4e	.
=9	=9
2d	G dominant
2g	.
=10	=10
[1e	C major
=11	=11
2e]	.
!!LO:TX:a:t=N.C.
4c	.
4d	.
=12:|!	=12:|!
2d	G dominant
2e	.
=13	=13
[1c	C major
=14	=14
2c]	F major
4c	C major
!!LO:TX:a:t=N.C.
4e	.
=15	=15
2.d	D minor
4e	.
=16	=16
2.f	G dominant
4d	.
=17	=17
2.e	C major
4f	.
=18	=18
2g	C dominant
4g	.
4g	.
=19	=19
2a	F major
2a	.
=20	=20
2cc	.
4b	.
4a	.
=21	=21
[1g	C major
=22	=22
2g]	G dominant
!!LO:TX:a:t=N.C.
4c	.
4d	.
=23	=23
2e	C major
4e	.
4g	.
=24	=24
2f	G dominant
4f	.
4a	.
=25	=25
4.g	C major
8a	.
4g	.
4f	.
=26	=26
2.e	.
4e	.
=27	=27
4.g	.
8a	.
4g	.
4f	.
=28	=28
2e	.
4e	.
4g	.
=29	=29
2f	D minor
4f	.
4e	.
=30	=30
2d	G dominant
2e	.
=31	=31
[1c	C major
=32	=32
2c]	F major
2r	C major
==	==
*-	*-
</script>




