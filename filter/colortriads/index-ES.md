---
title: filtro colortriads
lang: en es
ref: filters-colortriads
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 10 Sep 2020
translation_date: 8 aug 2021
last_updated: 10 Sep 2020
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
datatable: "true"
keywords: color triad command
summary: "Colorea las sonoridades triádicas diatónicas por el tono/función de la fundamental."
permalink: /filter/colortriads/index-ES.html
---
El filtro `colortriads` asigna colores a las sonoridades verticales según su fundamental triádica diatónica.  Los colores se asignan utilizando los colores del arco iris asignados al círculo de quintas, con el Do centrado en el centro en verde:

{% include image.html
	file="color-to-pitch.png"
	alt="Mapeo de color a tono"
	caption="Mapeo de color a tono para las sonoridades de las tríadas."
%}



{% include verovio.html
	source="chords"
	humdrum-min-height="225px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="chords">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads
</script>

El color verde representa las sonoridades verticales con las tres clases de tono diatónico Do, Mi y Sol. Cualquier alteración cromática de estas clases de tono también recibe un color verde, como Do, Mi bemol, Sol, o Do sostenido, Mi, Sol bemol.

{% include verovio.html
	source="cchords"
	humdrum-min-height="250px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="cchords">
**kern
4c 4e 4g
4cc 4e 4g
4cc 4g 4ee
4c 4g 4ee
4c 4e- 4g
4c# 4e- 4g#
4c# 4en 4g#
4c## 4e-- 4g# 4ee 4gg-
=
*-
!!!filter: colortriads
</script>

Aquí hay una [coral de Bach con sonoridades triádicas coloreadas](https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn&filter=colortriads%20%7C%20satb2gs):



{% include image.html
	file="chorale-2-pitch.png"
	alt="Tríadas coloreadas en el coral de Bach BWV 347"
	caption="Tríadas coloreadas en el coral de Bach BWV 347"
%}

Los movimientos de las fundamentales de los círculos de quinta se visualizan en los colores del arcoiris, como en los compases 10&ndash;11, donde la secuencia de acordes de Mi mayor, Si menor y Fa sostenido menor se muestra en los colores rojo, naranja y amarillo.  Si observamos los acordes del calderón, la mayoría son rojos, indicando Mi mayor (V), con uno naranja en Si menor (ii), y el último acorde en morado, indicando La mayor (I).

Las sonoridades no triádicas se dejan sin colorear.  Normalmente se trata de notas no armónicas y acordes de séptima en los corales.  Ocasionalmente, una nota estará en dos o más sonoridades triádicas separadas, como al principio del compás 6, donde el tiempo de ataque es un acorde de Re mayor, y las notas de paso crean una sonoridad de Sol disminuido:


{% include verovio.html
	source="double"
	tabsize="12"
	humdrum-min-height="150px"
	humdrum-min-width="400px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="double">
**kern	**kern	**kern	**kern
*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]
4D	4d	8f#L	8aL
.	.	8g#J	8bJ
*-	*-	*-	*-
!!!filter: colortriads | satb2gs
</script>
En estos casos, los tonos compartidos entre sonoridades sólo recibirán un color, dependiendo de la fundamental triádica a la que se le haya asignado el color primero.

## Coloreado funcional ##
Añadiendo la opción `-r` (que significa "relativa") se colorearán en cambio las sonoridades triádicas por función, utilizando el verde como tónica:

{% include image.html
	file="color-to-function.png"
	alt="Color-to-function mapping"
	url="https://verovio.humdrum.org/?file=chorales/chor002.krn&filter=colortriads%20%7C%20satb2gs"
	caption="Asignación de colores a funciones para las sonoridades de las tríadas cuando se añade la opción '-r'."
%}

Se necesita una designación de tonalidad inicial, como `*a:` para La menor, para identificar la tónica.  

{% include verovio.html
	source="achords"
	humdrum-min-height="250px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="achords">
**kern
*a:
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -r
</script>

Alternativamente, se puede utilizar la opción `-k` para proporcionar una designación de clave si no hay ninguna en los datos:

{% include verovio.html
	source="echords"
	humdrum-min-height="225px"
	humdrum-min-width="275px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="echords">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -r -k e
</script>

Ahora el Mi es tratado como el tónica.

Aquí hay un ejemplo de [el mismo coral de Bach con coloración funcional](https://verovio.humdrum.org/?file=chorales/chor002.krn&filter=colortriads%20-r%20%7C%20satb2gs):

{% include image.html
	file="chorale-2-function.png"
	alt="Tríadas de colores funcionales en el coral de Bach BWV 347"
	caption="Tríadas de colores funcionales en el coral de Bach BWV 347"
%}

Ahora las sonoridades del calderón en los acordes de la dominante están coloreadas en azul claro, la supertónica en azul oscuro y la tónica en verde.

Esta coloración funcional permite una comparación más fácil de las funciones de los acordes entre las piezas en diferentes tonos.  Puedes [desplazarte por los corales](https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn&filter=colortriads%20-r%20%7C%20satb2gs) con los botones de flecha situados en la parte superior izquierda de la ventana de VHV, o utilizar <span class="keypress">mayúsculas-derecha</span> y <span class="keypress">mayúsculas-izquierda</span> para navegar por el repertorio de corales de Bach de VHV.

## Cambio de colores ##
Las asignaciones de color se pueden cambiar con las opciones `-a` a `-g`.  Aquí hay un ejemplo de cambio de triadas C de verde a fuscia:


{% include verovio.html
	source="fuchsia"
	humdrum-min-height="225px"
	humdrum-min-width="300px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="fuchsia">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -c fuchsia
</script>
Se puede utilizar cualquier [color SVG](https://www.december.com/html/spec/colorsvg.html), así como los [códigos de color HTML](https://htmlcolorcodes.com).  Para cambiar el color de las sonoridades A, utiliza `-a`, para las sonoridades B usa `-b`, y así sucesivamente.

## Supresión de colores ##
Utiliza las opciones de `-A` a `-G` para suprimir la coloración de las tríadas que contengan esa fundamental.  Las opciones de una sola letra pueden pegarse entre sí, por lo que la opción `-ABC` del ejemplo siguiente es equivalente a `-A -B -C`:

{% include verovio.html
	source="suppress"
	humdrum-min-height="225px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="suppress">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -ABC
</script>

## Coloreado extendido ##
El filtro colortriads es un front-end del filtro [msearch](/filters/msearch).  Utilizando la versión de línea de comandos de colortriads, puedes extraer las llamadas al filtro msearch añadiendo la opción `--filters`:

```bash
colortriads --filters file.krn
```

La configuración por defecto producirá esta salida:

```
!!!filter: msearch -p (=ace) -m V --color darkviolet
!!!filter: msearch -p (=bdf) -m Z --color darkorange
!!!filter: msearch -p (=ceg) -m @ --color limegreen
!!!filter: msearch -p (=dfa) -m "|" --color royalblue
!!!filter: msearch -p (=egb) -m j --color crimson
!!!filter: msearch -p (=fac) -m + --color gold
!!!filter: msearch -p (=gbd) -m N --color skyblue
```
Hay siete llamadas a msearch, una por cada fundamental triádica a colorear.  La opción `--color` establece el color, que es rojo por defecto. La opción `-m` se utiliza para especificar el significante de usuario que marcará la nota (y hará que se coloree).  Puede ser un carácter del conjunto "NVZ@|+ijl", además de otros con diferentes grados de éxito, como los caracteres del conjunto "kKhPps".  Ten en cuenta que los caracteres de marca deben ser únicos; de lo contrario, las diferentes asignaciones de color con una marca compartida se colapsarán a uno de esos colores.  Los caracteres Unicode pueden estar permitidos (o lo estarán en el futuro).

La opción `-p` da el patrón de tono a buscar.  El patrón `(=ace)` significa buscar una sonoridad vertical que contenga una o más de cada una de las tres clases de tono A, C y E. Los paréntesis indican una búsqueda armónica (en lugar de una búsqueda melódica), y el signo de igualdad requiere que sólo las clases de tono enumeradas estén presentes en la sonoridad (sin el signo de igualdad, se permiten otras clases de tono).

Si quieres refinar la coloración, puedes copiar los filtros anteriores como plantilla para colorear de varias maneras.  Por ejemplo, para colorear las triadas de La menor de color violeta oscuro y las triadas de La mayor de color morado medio, utiliza estos dos comandos:


```
!!!filter: msearch -p (=ancnen) -m N --color darkviolet
!!!filter: msearch -p (=anc#en) -m V --color mediumpurple
```



{% include verovio.html
	source="majorminor"
	humdrum-min-height="150px"
	humdrum-min-width="475px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="majorminor">
**kern
4a 4cc 4ee
4a 4cc# 4ee
=
*-
!!!filter: msearch -p (=ancnen) -m N --color darkviolet
!!!filter: msearch -p (=anc#en) -m V --color mediumpurple
</script>

La consulta "ancnen" significa La-natural, Do-natural y Mi-natural, con espacio entre notas opcional.  Al dar una alteración cromática a una clase de tono diatónico, sólo se coloreará esa variante, lo que permite asignar colores diferentes a los acordes mayores y menores.

De manera similar, los acordes de séptima dominante podrían colorearse:

{% include verovio.html
	source="domsev"
	humdrum-min-height="175px"
	humdrum-min-width="450px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="domsev">
**kern
4c 4e 4g
4g 4b 4dd
4g 4b 4dd 4ff
=
*-
!!!filter: colortriads
!!!filter: msearch -p (=gnbndnfn) -m l --color fuchsia
</script>

To view the command-line commands rather than as filters,
use the `--commands` option:


```bash
colortriads --commands file.krn
```

```
msearch -p (=ace) -m V --color darkviolet
msearch -p (=bdf) -m Z --color darkorange
msearch -p (=ceg) -m @ --color limegreen
msearch -p (=dfa) -m "|" --color royalblue
msearch -p (=egb) -m j --color crimson
msearch -p (=fac) -m + --color gold
msearch -p (=gbd) -m N --color skyblue
```


## Limitaciones ## 
El coloreado se limita actualmente a las partes monofónicas, con capacidades limitadas para colorear acordes y partes con subcolumnas (con varias voces), como es habitual en la música de piano.  La capacidad de colorear estas texturas se añadirá en el futuro.
