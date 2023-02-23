---
title: filtro shed
lang: en es
page_language: es
translator: David Rizo
translation_date: 9 Aug 2021
translation_update:
ref: filters-shed
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/shed/index-ES.html
---
El filtro shed es un editor de expresiones regulares para manipular el contenido de los datos de Humdrum.  Es similar a la herramienta <a target="_blank" href="https://en.wikipedia.org/wiki/Sed">sed</a>, y el nombre significa "Streamed Humdrum EDitor" en homenaje.  El filtro shed también está relacionado con el comando Humdrum Toolkit <a target="_blank" href="https://www.humdrum.org/man/humsed">humsed</a>, pero tiene una interfaz lo suficientemente novedosa como para justificar un nombre diferente.  La principal diferencia entre shed y humsed es que shed evita automáticamente la ruptura de la estructura de archivos de Humdrum cuando se aplican sustituciones.

La sintaxis de las expresiones regulares utilizadas por el filtro shed coincide con la de <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions">javascript</a>, que a su vez es casi idéntica a las expresiones regulares de PERL.  En otras palabras, es una forma de expresiones regulares extendidas, por lo que caracteres como `+` funcionan como metacaracteres además de los operadores básicos de las expresiones regulares.

## Eliminación de articulaciones ##
He aquí un ejemplo de aplicación de shed para eliminar las articulaciones de los datos de \*\*kern:


{% include verovio.html
	source="artic"
	scale="50"
	pageWidth="1250"
	tabsize="10"
%}
<script type="application/x-humdrum" id="artic">
**kern
*M4/4
=1
4c'
4d~
4e'~
4f^
=2
4g^^
4ao
4b`
4cc;
==
*-
</script>
El filtro shed requiere una opción, `-e`, que contiene una cadena de sustitución de expresiones regulares similar a sed.  La estructura de la sustitución es la siguiente:

```
s/search/replacement/options
```
donde "s" es un carácter literal que indica una sustitución.  El carácter que sigue a la "s" se utiliza para separar tres parámetros para la sustitución: la expresión de búsqueda, luego la cadena de sustitución que se utilizará cuando el patrón de búsqueda coincida y, por último, una lista de opciones para la sustitución.

Este comando se inserta en una cadena dada al programa con la opción `-e`, que significa "expresión (regular)".  Así que para eliminar las articulaciones del ejemplo anterior, es necesario eliminar los caracteres "~'^`o;", por lo que el comando de sustitución será:

```
s/['~^o`;]//g
```

Esta expresión significa eliminar de los datos de entrada todos los caracteres que se encuentran entre los corchetes.  Observa la "g" al final de la sustitución, esto significa seguir aplicando múltiples sustituciones en una línea; de lo contrario, sólo se sustituirá la primera coincidencia en una línea.  He aquí un ejemplo completo y la notación resultante de la eliminación de las articulaciones:

{% include verovio.html
	source="noartic"
	scale="50"
	humdrum-min-width="300"
	pageWidth="1250"
	tabsize="10"
%}

<script type="application/x-humdrum" id="noartic">
!!!filter: shed -e "s/['~^o`;]//g"
**kern
*M4/4
=1
4c'
4d~
4e'~
4f^
=2
4g^^
4ao
4b`
4cc;
==
*-
</script>

Las comillas alrededor de la cadena dada a `-e` son opcionales a menos que haya un espacio en la cadena.  Sin embargo, es conveniente poner comillas alrededor de la cadena de sustitución cuando se ejecuta la herramienta shed en la línea de comandos.

## Intercambio de articulaciones (sustituciones múltiples) ##
La cadena de expresión puede contener más de una operación de sustitución.  Separa cada una con dos puntos y/o un espacio:


```
s/search1/replacement1/options1; s/search2/replacement2/options2
```
He aquí un ejemplo en el que los staccatos y los tenutos se intercambian utilizando tres sustituciones: la primera convierte los staccatos en una cadena ficticia, la segunda convierte los tenutos en staccatos y la tercera convierte la cadena ficticia en tenutos:

```
s/'/ZZZ/g; s/~/'/g; s/ZZZ/~/g
```
En aras de la brevedad, se puede omitir el separador de punto y coma (a diferencia de sed):


```
s/'/ZZZ/g s/~/'/g s/ZZZ/~/g
```
En este caso, la cadena de sustitución contiene espacios, por lo que se requieren comillas en el filtro.  Ten en cuenta también que el uso de comillas simples o dobles dentro de una cadena de sustitución también requiere comillas alrededor de la cadena de opciones.

{% include verovio.html
	source="swapartic"
	scale="50"
	humdrum-min-width="400"
	humdrum-min-height="300"
	pageWidth="800"
	tabsize="10"
%}

<script type="application/x-humdrum" id="swapartic">
!!!filter: shed -e "s/'/ZZZ/g s/~/'/g s/ZZZ/~/g'"
**kern
*M4/4
=1
4c'
4d'
4e'
4f'
=2
4g~
4a~
4b~
4cc~
==
*-
</script>

El mismo resultado se puede conseguir con tres filtros distintos, aunque esto sería más lento, ya que los datos de Humdrum tienen que volver a analizarse dos veces más:

{% include verovio.html
	source="three"
	scale="50"
	humdrum-min-width="400"
	humdrum-min-height="325"
	pageWidth="800"
	tabsize="10"
%}

<script type="application/x-humdrum" id="three">
!!!filter: shed -e "s/'/ZZZ/g"
!!!filter: shed -e "s/~/'/g"
!!!filter: shed -e "s/ZZZ/~/g"
**kern
*M4/4
=1
4c'
4d'
4e'
4f'
=2
4g~
4a~
4b~
4cc~
==
*-
</script>






## Ámbito de sustitución ##
La principal diferencia entre sed y shed, es que shed contiene opciones de sustitución adicionales para controlar qué componente de los datos de Humdrum debe ser procesado.  El comportamiento por defecto es cambiar sólo los tokens de datos, ignorando otras partes de los archivos Humdrum, como los comentarios globales y las interpretaciones de tipo tándem.

Aquí hay una lista de los operadores adicionales que se pueden dar para las sustituciones dentro de otros componentes de los archivos de Humdrum:

Carácter | Significado
==========|==========
I         | Sólo se hacen sustituciones en las interpretaciones tipo tándem.
X         | Sólo se hacen sustituciones en interpretaciones exclusivas.
L         | Sólo se hacen sustituciones en los comentarios locales.
D         | Sólo se hacen sustituciones en los tokens de datos.
B         | Sólo se hacen sustituciones en los tokens de líneas de compás.
R         | Sólo se hacen sustituciones en registros de referencia.
K         | Sólo se hacen sustituciones en las claves de los registros de referencia.
V         | Sólo se hacen sustituciones en los valores de los registros de referencia.

Si especifica otro componente de Humdrum, como `I` para interpretaciones tipo tándem, los tokens de datos ya no serán procesados.  Si todavía quieres que los tokens de datos sean procesados junto con otro componente Humdrum, añade explícitamente la opción `D`, como `ID` para procesar tanto las interpretaciones en tándem como los tokens de datos.


### Convertir **kern en **recip ###

He aquí un ejemplo de uso de shed para convertir los datos \*\*kern en datos \*\*recip:


```
!!!filter: shed -e "s/[^\d.%_\][]//gk s/kern/recip/X"
```

### Etiquetas para los colores ###

Este es un ejemplo que convierte un marcador de interpretación arbitrario en un código de color:


{% include verovio.html
	source="marker"
	scale="50"
	humdrum-min-width="525"
	pageWidth="750"
	tabsize="10"
%}
<script type="application/x-humdrum" id="marker">
!!!filter: shed -e "s/up/color:red/I s/down/color:dodgerblue/I"
**kern	**kern
*M4/4	*M4/4
=1	=1
*up	*down
4c	4cc
4d	4b
4e	4a
4f	4g
=2	=2
4g	4f
4a	4e
4b	4d
4cc	4c
=3	=3
*down	*up
4b	4d
4a	4e
4g	4f
4f	4g
=4	=4
4e	4a
4d	4b
2c;	2cc;
==	==
*-	*-
</script>

Este uso del shed permite codificar en la partitura digital sólo el marcado simbólico/analítico, y a partir de él se genera automáticamente el marcado visual para generar la notación gráfica.



## Selección por tipo de datos  ##
Hay una opción de sustitución especial `k` que sólo procesará las columnas de \*\*kern e ignorará cualquier otro tipo de columna.  También hay una opción `-k` que se puede utilizar con el filtro shed.  La diferencia entre ambas es que la opción `-k` se aplicaría a todas las sustituciones de la opción `-e`, mientras que la opción `k` sólo se aplicaría a una sustitución específica.

Ningún otro tipo de datos de la columna tiene una operación de sustitución, pero existe un mecanismo por el cual se puede asociar una opción de sustitución a un tipo de datos específico.  Las letras de opción `X`, `Y` y `Z` pueden asignarse a tipos de datos concretos mediante las opciones de shed `-X`, `-Y` y `-Z`.  He aquí un ejemplo:

```
!!!filter: shed -X text -Y dynam -e "s/f/p/gY s/[aeio]/u/gX"
```

Esto significaría cambiar todos los caracteres "f" por "p", pero sólo en los datos de la columna \*\*dynam, y luego sustituir las vocales `a`, `e`, `i` y `o` por `u` sólo en los datos de la columna \*\*text.

Un método alternativo para seleccionar los tipos de datos específicos que se van a procesar se realiza mediante la opción -i.  Ten en cuenta que este método se aplica a todas las operaciones de sustitución.  Ejemplo:

```
!!!filter: shed -i "text,dynam" -e "s/f/p/g s/[aeio]/u/g"
```
Esto significa cambiar `f` por `p` y `[aeio]` por `u` sólo en las columnas \*\*text y \*\*dynam.  Los cambios se producirán en ambos tipos de columna, por lo que si hay una `f` en la columna \*\*text, se convertirá en una `p`.




