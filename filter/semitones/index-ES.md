---
title: filtro semitones
lang: en es
ref: filters-semitones
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 15 Nov 2020
translation_date: 8 Aug 2021
last_updated: 15 Nov 2020
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/semitones/index-ES.html
---
El filtro semitones calcula los intervalos de semitonos melódicos para las notas de la columna (*spine*) del `**kern`.  El filtro también puede utilizarse para resaltar tonos, saltos, repeticiones y direcciones de intervalo en la notación renderizada.



## Opciones ##

| opción | descripción  |
| ------ | -----------  |
| -c     | Almacena los análisis en columnas de `**cdata`, que se muestran como texto encima de los pentagramas en notación renderizada. |
| -d     | Resalta/cuentta sólo los intervalos descendentes. |
| -j #   | Establece el valor del semitono para el límite entre tonos y saltos (por defecto: 3). |
| -l     | Resalta/cuenta sólo los saltos. |
| -m     | Extrae números de notas MIDI en lugar de semitonos. |
| -n     | Incluye el recuento de intervalos resaltados en los datos de salida. |
| -r     | Resalta/cuenta notas repetidas. |
| -s     | Resalta/cuenta tonos. |
| -u     | Resalta/cuenta intervalos ascendentes. |
| -x *expr* | Excluye las notas que coinciden con las expresiones regulares. |
| -A     | No se emiten columnas de análisis. |
| -I     | No incluye los datos de entrada en los de salida. |
| -M     | No se marca ninguna nota. |
| -R     | Ignora los silenciios. |
| -T     | No resalta las notas secundarias ligadas. |
| -X     | Sólo calcula los intervalos que comienzan en los tokens que contienen la expresión. |
| -1     | Sólo resalta la primera nota de los intervalos marcados. |
| -2     | Sólo resalta la segunda nota de los intervalos marcados. |
| --color *cadena* | Establece el color de las notas marcadas. |
| --mark  *carácter*   | Establece el carácter del significante para las notas marcadas. |


## Visualización de los intervalos de semitono ##
La salida por defecto del filtro semitones crea una columna (*spine*) `**tti` (intervalo de doce tonos) después de cada columna `**kern`.   Este análisis no se imprime en la notación renderizada.   Para ver el análisis de los intervalos de semitonos en la notación, añade la opción `-c` para que el análisis salga en columnas de `**cdata` (es decir, datos "tipo acorde" o *chord data*) que se mostrarán encima de la notación.


{% include verovio.html
	source="example1"
	scale="50"
	humdrum-min-width="180"
	spacingSystem="20"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example1">
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>
Observa que el intervalo de semitono melódico se muestra en la primera nota del intervalo.  Prueba a editar el texto musical de la izquierda para ver cómo cambia el análisis en la notación gráfica de la derecha.


## Resaltar categorías de intervalos ##
Las siguientes opciones pueden utilizarse para resaltar grupos de intervalos:

| opciones | significados |
| ------ | ------- |
| -u     | Resalta sólo las notas que intervienen en los intervalos ascendentes. |
| -d     | Resalta sólo las notas que intervienen en los intervalos descendentes. |
| -r     | Resalta sólo las notas repetidas. |
| -s     | Resalta sólo las notas que intervienen en el movimiento por grados conjuntos. |
| -l     | Resalta sólo las notas que intervienen en el movimiento de salto. |

A continuación se ofrecen ejemplos de varias opciones de resaltado.

### Resaltar las notas repetidas ###

Si se añade la opción '-r', se resaltan las notas que se repiten.


{% include verovio.html
	spacingSystem="20"
	source="example-repeat"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-repeat">
!!!filter: semitones -rc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

### Resaltar los intervalos ascendentes ###

Añadiendo la opción '-u' se resaltan las notas que crean intervalos de semitono ascendente.


{% include verovio.html
	spacingSystem="20"
	source="example-up"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-up">
!!!filter: semitones -uc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

### Resaltar los intervalos descendentes ###
Si se añade la opción `-d`, se resaltarán las notas que crean intervalos de semitono descendente.

{% include verovio.html
	spacingSystem="20"
	source="example-down"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-down">
!!!filter: semitones -dc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


### Resaltar los intervalos de grado conjunto ###

Si se añade la opción `-s`, se resaltarán las notas que crean intervalos de grado conjunto.

{% include verovio.html
	spacingSystem="20"
	source="example-step"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-step">
!!!filter: semitones -sc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


### Resaltar los intervalos de salto ###
Si se añade la opción `-l`, se resaltan las notas que crean saltos melódicos.

{% include verovio.html
	spacingSystem="20"
	source="example-leap"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-leap">
!!!filter: semitones -lc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

El límite entre saltos y grado conjunto es `3` por defecto (el salto más pequeño es de tres semitonos, o una tercera menor).  Para cambiar el límite entre saltos y grado conjunto utiliza la opción `-j` (que significa "salto" o "*jump*") seguida del tamaño mínimo del salto, como `-j4`, que definirá un `3` (tercera menor) como un grado conjunto.  Para que el ejemplo sea claro, la opción `-1`, se utiliza a continuación para resaltar sólo la primera nota que crea los intervalos:

{% include verovio.html
	spacingSystem="20"
	source="example-leap2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-leap2">
!!!filter: semitones -lc1j4
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>



### Resaltar las mezclas de grupos de intervalos ###
Las opciones de intervalo ascendente/descendente pueden emparejarse con los intervalos de paso/graado conjunto para destacar los intervalos que satisfacen ambos requisitos:

| opciones | significado |
| `-us`   | resalta los intervalos ascendentes por grado conjunto.   |
| `-ds`   | resalta los intervalos descendentes por grado conjunto.   |
| `-ul`   | resaltar los intervalos de saltos ascendentes.   |
| `-dl`   | resaltar los intervalos de saltos descendentes.   |

Este es un ejemplo de cómo resaltar sólo los intervalos ascendentes por grado conjunto:

{% include verovio.html
	spacingSystem="20"
	source="example-mix-step"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-mix-step">
!!!filter: semitones -usc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

Y saltos descendentes:


{% include verovio.html
	spacingSystem="20"
	source="example-mix-leap"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-mix-leap">
!!!filter: semitones -dlc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>



## Resaltar sólo una nota de intervalo ##

La opción `-1` puede utilizarse para resaltar sólo la primera nota de un par de intervalos:


{% include verovio.html
	spacingSystem="20"
	source="example-first"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-first">
!!!filter: semitones -s1c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

y `-2` resalta sólo la segunda nota del intervalo:

{% include verovio.html
	spacingSystem="20"
	source="example-second"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-second">
!!!filter: semitones -s2c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


## Estilo de resaltado ##

Varios grupos de intervalos pueden ser resaltados en diferentes colores utilizando las opciones `--mark` y `--color`.  Ambas deben ser especificadas para marcar los intervalos con diferentes colores.

He aquí un ejemplo en el que se utilizan los marcadores por defecto `@` y el color rojo para los saltos hacia arriba, y luego se utiliza un marcador diferente para indicar un color distinto para los saltos hacia abajo:

{% include verovio.html
	spacingSystem="20"
	source="example-color"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-color">
!!!filter: semitones -u -l -A -1
!!!filter: semitones -dl1 --mark Z --color dodgerblue
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


## Rests ##

Por defecto, los intervalos no se calculan a través de los silencios:

{% include verovio.html
	source="example-rest"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-rest">
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4r
=
4f
4g
4a
4b
=
*-
</script>


Añadiendo la opción `-R`, los silencios serán ignorados:

{% include verovio.html
	source="example-norest"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-norest">
!!!filter: semitones -cR
**kern
*M4/4
=1
4c
4d
4e
4r
=
4f
4g
4a
4b
=
*-
</script>


## Exclusión/inclusión de notas ##
La opción `-x` puede utilizarse para evitar que se calcule un intervalo basado en un patrón de expresión regular.  Este es un ejemplo en el que se suprime el intervalo después de un calderón:


{% include verovio.html
	spacingSystem="20"
	source="example-nofermata"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-nofermata">
!!!filter: semitones -c -x ';'
**kern
*M4/4
=1
4c
4d
4e
4f;
=
4g
4a
4b
4cc
=
*-
</script>
Nótese que el intervalo del calderón es `x`, lo que significa que se excluye del análisis.  Esto es útil para utilizarlo como límite de segmentación para el post-procesamiento de los intervalos extraídos.  Cuando la cadena es un punto y coma (`;`), las comillas alrededor de la expresión de exclusión no tienen que estar entre comillas, pero si el filtro se utiliza en la línea de comandos, las comillas son necesarias.

La opción `-X` invierte la exclusión, y sólo se analizarán los tokens de notas que contengan la expresión regular especificada:

{% include verovio.html
	spacingSystem="20"
	source="example-onlyfermata"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-onlyfermata">
!!!filter: semitones -c -X ';'
**kern
*M4/4
=1
4c
4d
4e
4f;
=
4g
4a
4b
4cc
=
*-
</script>

Así que este ejemplo sólo calcula los intervalos que comienzan en las notas del calderón.


## Ejemplos VHV ##

He aquí un ejemplo que utiliza los siguientes filtros para resaltar cada clase de intervalo refinado:

```
!!!filter: semitones -ul2A
!!!filter: semitones -dl2A --mark j --color hotpink
!!!filter: semitones -us2A --mark V --color dodgerblue
!!!filter: semitones -ds2A --mark Z --color blue
!!!filter: semitones -r2A --mark + --color limegreen
!!!filter: satb2gs
```
Pruebaa a copiar y pegar las líneas de filtro anteriores en VHV para el ejemplo [coral de Bach](http://verovio.humdrum.org/?file=chorales/chor001.krn) utilizado a continuación.

La opción `-2` se utiliza para resaltar sólo la segunda nota del intervalo.  Esto significa que el color indica el intervalo de aproximación.  Puede intentar cambiar esto a `-1` para que el color indique el intervalo de salida.  La opción `-A` se utiliza para evitar que se generen múltiples columnas de análisis de salida duplicadas.  Esto es opcional, ya que las columnas de análisis no se muestran en la notación gráfica.

{% include note.html
	content="Ten en cuenta que cada categoría debe tener una marca única, ya que la coloración se produce a través de estas marcas.  Si dos grupos tienen el mismo grupo, sólo se puede utilizar un color para ambos grupos."
%}


{% include image.html
	file="refinedcontour.png"
	url="http://verovio.humdrum.org/?file=chorales/chor001.krn&filter=semitones%20-ul2A|semitones%20-dl2A%20--mark%20j%20--color%20hotpink|semitones%20-us2A%20--mark%20V%20--color%20dodgerblue|semitones%20-ds2A%20--mark%20Z%20--color%20blue|semitones%20-r2A%20--mark%20+%20--color%20limegreen|satb2gs"
	alt="Resaltar las categorías de grados conjuntos/saltos"
	caption="Resaltar las categorías de grados conjuntos/saltos mediante el filtro de semitonos"
	margin-bottom="-20px"
%}

Haz clic en la imagen para cargar la partitura y los filtros de resaltado en VHV.  A continuación, utiliza los botones de flecha izquierda/derecha de la parte superior de la página para navegar por otros corales con los intervalos resaltados.

Prueba a añadir `-x ';'` a cada filtro semitones para ignorar los intervalos después de los calderones.

Prueba a añadir `-j 5` para que los saltos se definan como cuartas o intervalos mayores.


## Número de notas MIDI ##

Añadiendo la `-m` se extraerán los números de las notas MIDI en lugar de los intervalos de semitono:

{% include verovio.html
	spacingSystem="20"
	source="example-midi"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-midi">
!!!filter: semitones -cm
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

He aquí un ejemplo de extracción tanto de los números de nota MIDI como de los intervalos de semitono:

{% include verovio.html
	spacingSystem="20"
	source="example-midisemi"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-midisemi">
!!!filter: semitones -cm
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

Observa que el número de nota MIDI más el intervalo de semitono que hay debajo da el número de nota de la siguiente nota.

## Cómo tratar con los acordes ##
Cuando hay acordes en los datos de entrada, sólo se considerará la primera nota del acorde.  Si no conoces el orden de las notas del acorde, o quieres forzar que se utilice la nota más alta o más baja del acorde, utiliza el filtro *chord* para ordenar las notas del acorde antes del análisis.

Aquí hay un ejemplo en el que las notas de los acordes están mezcladas, y los intervalos entre la nota única y el acorde cambian en cada compás debido a la ordenación acorde-nota:

{% include verovio.html
	spacingSystem="20"
	source="example-chord1"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord1">
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>

Ordenación de las notas de los acordes de mayor a menor, utilizando la opción `-d` (descendente):

{% include verovio.html
	spacingSystem="20"
	source="example-chord2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord2">
!!!filter: chord -d
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>


Ordenación de las notas de los acordes de menor a mayor, utilizando la opción `-u` (ascendente):

{% include verovio.html
	spacingSystem="20"
	source="example-chord3"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord3">
!!!filter: chord -u
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>

Si no quieres que se muestren las notas de los acordes que no se utilizan en el análisis de semitonos, utilizaa la opción `-f` (que significa "primera" o "*first*") para el filtro de acordes para mantener sólo la primera nota del acorde.  Para ordenar las notas antes de tomar la primera nota, utiliza `-t` para seleccionar la nota superior (más alta), o `-b` para seleccionar la nota inferior (más baja) de cada acorde.


{% include verovio.html
	spacingSystem="20"
	source="example-chord4"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord4">
!!!filter: chord -t
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>

{% include verovio.html
	spacingSystem="20"
	source="example-chord5"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord5">
!!!filter: chord -b
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>



## Uso de líneaa de comando ##
Cuando se utiliza en la línea de comandos sin opciones, se colocan columnas `**tti` (intervalo de doce tonos) después de cada columna `**kern` de la que se extrae el análisis:

```bash
humcat h://chorales/chor001.krn | semitones
```

```tsv
**kern	**tti	**kern	**tti	**kern	**tti	**kern	**tti
*Ibass	*Ibass	*Itenor	*Itenor	*Ialto	*Ialto	*Isoprn	*Isoprn
*clefF4	*clefF4	*clefGv2	*clefGv2	*clefG2	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4
4GG	12	4B	0	4d	0	4g	0
=1	=1	=1	=1	=1	=1	=1	=1
4G	-3	4B	1	4d	2	2g	7
4E	2	8cL	-1	4e	-2	.	.
.	.	8BJ	-2	.	.	.	.
4F#	1	4A	-2	4d	0	4dd	-3
=2	=2	=2	=2	=2	=2	=2	=2
4G	-5	4G	-1	2d	-3	4.b	-2
4D	2	4F#	1	.	.	.	.
.	.	.	.	.	.	8a	-2
4E	-4	4G	5	4B	5	4g	0
=3	=3	=3	=3	=3	=3	=3	=3
4C	-1	8cL	-1	8eL	-2	4.g	2
.	.	8BJ	1	8d	2	.	.
8BBL	-2	4c	2	8e	2	.	.
8AAJ	-2	.	.	8f#J	1	8a	2
4GG	7	4d	0	4g	-1	4b	-2
=4	=4	=4	=4	=4	=4	=4	=4
2D;	-7	2d;	0	2f#;	1	2a;	2
4GG	-1	4d	-5	4g	-5	4b	3
=5	=5	=5	=5	=5	=5	=5	=5
etc.
```


### Salida sólo de datos de análisis ###

Por defecto, los datos de salida incluyen todos los datos de entrada, insertando las columnas de análisis inmediatamente a la derecha de cada columna `**kern`.  Los datos de entrada pueden suprimirse en la salida añadiendo la opción `-I`, que significa "sin entrada":

```bash
humcat h://chorales/chor001.krn | semitones -I
```

```tsv
**tti	**tti	**tti	**tti
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M3/4	*M3/4	*M3/4	*M3/4
12	0	0	0
=1	=1	=1	=1
-3	1	2	7
2	-1	-2	.
.	-2	.	.
1	-2	0	-3
=2	=2	=2	=2
-5	-1	-3	-2
2	1	.	.
.	.	.	-2
-4	5	5	0
=3	=3	=3	=3
-1	-1	-2	2
.	1	2	.
-2	2	2	.
-2	.	1	2
7	0	-1	-2
=4	=4	=4	=4
-7	0	1	2
-1	-5	-5	3
=5	=5	=5	=5
etc.
```


### Histogramas de intervalos para los corales de Bach ###

Usando las herramientas humlib *humcat*, *serialize*, *ridx*, y *sortcount*, así como la herramienta unix *sort*:

```bash
humcat -s h://chorales | semitones -I | serialize | ridx -H | sortcount | sort -nrk2
```

```tsv
1	24
4	19
6	17
4	16
2	15
9	14
5	13
609	12
17	11
37	10
193	9
183	8
1086	7
34	6
4340	5
819	4
1038	3
15270	2
9924	1
731	r
11241	0
11157	-1
17503	-2
2065	-3
2245	-4
1589	-5
268	-6
2144	-7
116	-8
68	-9
16	-10
6	-11
461	-12
7	-14
```
La primera columna es el recuento de intervalos y la segunda columna contiene el intervalo de semitonos.  El intervalo más grande es `24` (dos octavas arriba), y el más común es `-2` (segunda mayor).

El siguiente ejemplo crea una página web que contiene un gráfico interactivo del histograma de semitonos para los corales de Bach:


```bash
humcat -s h://chorales | semitones -I | serialize | ridx -H \
     | sortcount -v --sort number -x semitones \
     -T "Bach chorale melodic semitones"  > output.html
```

{% include_relative plot.txt %}

Mueve el ratón sobre cada barra para ver el recuento de cada intervalo.


### Excluir los intervalos después de los calderones ###
Para evitar contar los intervalos después de las notas con calderones:


```bash
humcat -s h://chorales | semitones -Ix ';' | serialize \
     | ridx -H | sortcount | sort -nrk2
```

```tsv
2	17
274	12
4	11
13	10
77	9
75	8
784	7
23	6
3625	5
414	4
603	3
14715	2
9436	1
9363	0
9	r
10935	-1
17130	-2
1786	-3
2003	-4
1418	-5
249	-6
2029	-7
99	-8
55	-9
11	-10
2	-11
432	-12
6	-14
```

Contando sólo los intervalos entre los calderones y las siguientes notas/silencios:


```bash
humcat -s h://chorales | semitones -IX ';' | serialize \
     | ridx -H | sortcount | sort -nrk2
```

```tsv
1	24
9	19
2	18
13	17
14	16
10	15
27	14
14	13
380	12
30	11
71	10
151	9
163	8
404	7
77	6
827	5
489	4
541	3
656	2
561	1
752	r
2035	0
272	-1
459	-2
348	-3
291	-4
208	-5
38	-6
143	-7
28	-8
30	-9
10	-10
4	-11
30	-12
2	-14
```


```bash
humcat -s h://chorales | semitones -IX ';' | serialize \
     | ridx -H | sortcount -v --sort number -x semitones \
     -T "Intervals after fermatas" > output.html
```

{% include_relative plot2.txt %}


Las notas repetidas son más comunes después de los calderones.


### Secuencias de intervalos en los corales de Bach ###
He aquí un ejemplo de cómo identificar las secuencias de 5 intervalos más comunes en el repertorio coral de Bach:

```bash
humcat -s h://chorales | semitones -I | ridx -M \
   | serialize | context -n 5 | ridx -H | sortcount | head -n 20
```

```tsv
311	2 1 -1 -2 -2
271	-2 -2 -1 -2 2
262	2 2 1 -1 -2
246	2 1 2 -2 -1
243	1 2 -2 -1 -2
233	-2 -1 -2 2 1
227	-2 -2 -1 -2 -2
212	2 2 -2 -2 -1
203	-1 -2 -2 2 2
185	2 -2 -2 -1 -2
184	-1 -2 2 1 2
175	1 2 2 -2 -2
162	-2 -2 2 2 1
159	-2 2 1 -1 -2
150	-2 -1 -2 -2 2
147	-2 -1 1 -1 -2
147	-2 -2 -1 1 2
145	2 2 1 2 -2
144	2 1 -1 -2 2
137	-1 -2 2 1 -1
```
Las 20 secuencias de 5 intervalos más comunes son todas de tono, sin notas repetidas, silencios o saltos.


{% comment %}

## Pentagramas polifónicos ##
Cuando hay divisiones de columna, el análisis seguirá melódicamente ambas subcadenas.   Al dividir, se utilizará el camino más a la izquierda para calcular un intervalo hasta la nota anterior a la división.  Al unirse, varias subcolumnas pueden compartir la misma nota fusionada:

{ include verovio.html
	spacingSystem="20"
	source="example-poly"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
}
<script type="application/x-humdrum" id="example-poly">
!!!filter: semitones -c
**kern
*M4/4
4c
4d
*^
4e	4g
4f	4a
=	=
4cc	4b
*v	*v
4f
4d
4c
=
*-
</script>
{% endcomment %}


## Contar los intervalos resaltados ##
Añade la opción `-n` para contar los intervalos que se resaltan.  Esto añadirá una línea en la parte inferior de los datos con el recuento de intervalos seguido de las opciones utilizadas para seleccionar pasos, saltos, hacia arriba, hacia abajo, etc.

Por ejemplo, dados los datos de entrada:

```tsv
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
```

The command/filter:

```bash
semitones -uln
```

contará el número de saltos hacia arriba:

```tsv
**kern	**tti
*M4/4	*M4/4
=1	=1
4c	2
4d	2
4e	1
4f	-5
=	=
@4c	4
@@4e	3
@@4g	5
@4cc	0
=	=
4cc	-1
4b	-2
4a	-2
@4g	5
=	=
@4cc	-5
4g	-3
4e	-4
4c	.
=	=
*-	*-
!!!RDF**kern: @ = marked note
!!semitone_count: 4 UP LEAP
```

The line

```
!!semitone_count: 4 UP LEAP
```

significa que hubo cuatro saltos ascendentes en el ejemplo.


La opción `-M` puede utilizarse para no marcar ninguna nota en las columnas de `**kern`, y `-A` puede utilizarse para no emitir las columnas de análisis.   Estas opciones harán que sólo se añada la línea `semitone_count` a los datos de entrada:

```bash
semitones -ulnMA
```

```tsv
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
!!semitone_count: 4 UP LEAP
```

Si sólo deseas el recuento de intervalos, utiliza el comando

```bash
semitones -uln input.krn | awk 'END {print $2}'
```

que en este caso devolverá `4`.





