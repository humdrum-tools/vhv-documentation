---
title: Filters
lang: en es
ref: filters
author: Craig Stuart Sapp
translator: 
creation_date: 31 Aug 2020
translation_date: 
last_updated: 23 Apr 2020
tags: [all, filters]
sidebar: main_sidebar
aton: "true"
verovio: "true"
keywords: interface commands 
summary:  "Documentación de los filtros en VHV."
permalink: /filter/index-ES.html
---

<script type="text/x-aton" id="example-data">
{% include_relative examples.aton %}
</script>

{% include_relative styles-local.html %}
{% include_relative listeners.html %}
{% include_relative scripts-local.html %}

Los filtros permiten manipular el contenido de los datos de Humdrum antes de
que se conviertan en notación.  También se pueden utilizar para manipular
los datos al preparar una partitura, como por ejemplo para añadir una nueva columna, o para
unir notas.

Como ejemplo de filtrado antes de pasar a la notación musical, una partitura
 gráfica puede ser transpuesta mientras se mantienen los datos de Humdrum en
el editor de texto en el tono original.  Aquí están los enlaces a la
<i>Sonata facile</i> de Mozart, que fue escrita en Do mayor pero puede ser
transpuesta a cualquier otra tonalidad:

<a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c-">Do♭ mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&toolbar=filter">Do&nbsp;mayor</a> (sin filtrar)
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c#">C#&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d">Re&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d-">Re♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e-">Mi♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e">Mi&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f">Fa&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f#">Fa#&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G-">Sol♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G">Sol&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A-">La♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A">La&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B-">Si♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B">Si&nbsp;mayor</a>

Observa en cada caso que los datos de Humdrum en el editor de texto permanecen en Do mayor.  Si quieres alterar los datos de Humdrum en el editor de texto, entonces escribe el atajo de teclado <span class="keypress">alt-c</span>.  Esto "compilará" los filtros en los datos y reemplazará los datos originales con los datos filtrados.  Aquí hay ejemplos en los que la música se muestra en cada tonalidad y los datos también se modifican para que coincidan con esa tonalidad:


<a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c-">Do♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&toolbar=filter">Do&nbsp;mayor</a> (sin filtrar)
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c#">Do#&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d">Re&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d-">Re♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e-">Mi♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e">Mi&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f">Fa&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f#">Fa#&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G-">Sol♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G">Sol&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A-">La♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A">La&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B-">Si♭&nbsp;mayor</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B">Si&nbsp;mayor</a>




## Barra de herramientas de filtros ##
En la esquina superior derecha de la interfaz de VHV hay una barra de herramientas de filtros:

<div style="margin-left: 50px;" class="toolbar" id="toolbar-5">
	<input id="filter"  onkeyup="checkForFilterActivate(event)" type="text" spellcheck="false" placeholder="filter">
	<div title="Apply filter" class='filter-icon nav-icon fa fa-filter'></div>
	<div id="filter-compile" title="Compile filter (alt-c)" class='nav-icon fa fa-plus'></div>
	<div title="About filterss" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br/>
Si no está visible ninguna barra de herramientas, pulsa <span class="keypress">alt-shift-N</span> para hacer visible la barra de herramientas, o pulsa <span class="keypress">alt-shift-E</span> para alternar la visualización del menú y de la barra de herramientas.  Si está visible una barra de herramientas diferente, haz clic en el icono circular de la derecha hasta que la barra de herramientas del filtro sea visible.  Se puede escribir el atajo de teclado <span class="keypress">5+alt-n</span> para mostrar la barra de herramientas de filtro directamente (es posible que tengas que hacer clic en el panel de notación musical para desenfocar el editor de texto; de lo contrario, se insertará un "5" en el texto).


### Uso de la barra de herramientas de filtros ###
Escribe un filtro en la caja de filtros.  A medida que escribas el filtro, no ocurrirá nada en la notación, ya que el filtro aún no se está aplicando.  Cuando hayas terminado de introducir el filtro, pulsa la tecla <span class="keypress">retorno</span> o haz clic en el icono del filtro situado a la derecha del cuadro de introducción de datos.  Esto hará que el icono del filtro se resalte en amarillo, lo que significa que el filtro se está aplicando a los datos:


<div style="margin-left:50px;" class="toolbar" id="toolbar-6">
	<input id="filter2"  onkeyup="checkForFilterActivate(event)" oninput="updateFilterState(event)" type="text" spellcheck="false" placeholder="transpose -k d">
	<div title="Apply filter" class='active filter-icon nav-icon fa fa-filter'></div>
	<div id="filter-compile" title="Compile filter (alt-c)" class='nav-icon fa fa-plus'></div>
	<div title="About filters" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon2">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br/>
Si escribe smás contenido en el cuadro de filtro, el icono del filtro dejará de resaltarse y el filtro dejará de aplicarse a los datos.  En tal caso, pulsa <span class="keypress">return</span> o haz clic en el icono del filtro para reactivarlo.  También puedes hacer clic en el icono de filtro amarillo para detener la aplicación del filtro antes de que los datos se conviertan en notación gráfica.


<table style="border-style: none !important; border-collapse: collapse !important; max-width: 100% !important; margin:0 !important; padding:0 !important;">
	<tr style="width:100%; padding:0; border: none !important; background:none !important;">
		<td style="border: none; width:100% !important; padding:0;">
Si deseas sustituir los datos originales de Humdrum en el editor de texto por los datos filtrados, haz clic en el icono
<div style="font-size:1rem; padding-left:3px; margin-top: -15px; padding-right: 3px; display:inline-block !important;" class="toolbar">
	<span style="display:inline-block !important;"  class='filter-icon nav-icon fa fa-plus'>
	</span>
</div>
o teclea <span class="keypress">alt-c</span> para "compilar" el filtro.
</td></tr></table>


## Filtros incrustados ##
En lugar de utilizar la interfaz de la barra de herramientas, también puedes escribir los comandos del filtro directamente en los datos de Humdrum.  Antepon al filtro el prefijo `!!!filter:`.  Cada línea de filtro encontrada en los datos será procesada en secuencia antes de mostrar la notación; por lo demás, la colocación de las líneas de filtro no es importante: pueden ir arriba, abajo o en algún lugar en medio de los datos.

Este es un ejemplo de incorporación de tres filtros distintos en los datos:

{% include image.html
	file="three-filters.jpg"
	alt="Incrustación de tres filtros."
	caption="Incorporación de tres filtros en los datos de Humdrum."
%}

Las tres primeras líneas de datos contienen los filtros:


```
!!!filter: myank -m 1-3
!!!filter: extract -i kern
!!!filter: transpose -t -m3
```
El filtro *myank* extrae los tres primeros compases de la partitura, el filtro *extract* elimina la letra de la partitura y *transpose* transpone la música una tercera menor.  Para utilizar los tres filtros desde la barra de herramientas, sepáralos con el carácter tubería (|).  Esto también puede hacerse para fusionar varios filtros en una sola línea de los datos:


```
!!!filter: myank -m 1-3 | extract -i kern | transpose -t -m3
```

{% include image.html
	file="combined-filters.png"
	alt="Combinación de tres filtros."
	caption="Combinación de tres filtros en la barra de herramientas del filtro."
%}


## Ejemplos por tema/filtro ##

Click on the blue filter text to load the filter into VHV and apply
to a sample piece of music.


### Transposición ###

El filtro [transposition](/filter/transposition) puede utilizarse para transponer la partitura de varias maneras que se ilustran a continuación.

<div data-category="transposition"></div>


### Filtros compuestos ###
A continuación se muestran ejemplos de cómo mezclar varios filtros.  Cada filtro 
se separa del siguiente con un carácter de tubería (|).

<div data-category="pipeline"></div>


### Extractos musicales ###
El filtro [myank](/filter/myank) puede utilizarse para extraer ejemplos musicales de partituras más largas.


<div data-category="excerpt"></div>



### Extracción de partes ###
El filtro [extract](/filter/extract) puede utilizarse para extraer partes y otros datos de una partitura completa.

<div data-category="extract"></div>




### Acordes ###

El filtro [chord](/filter/chord) se puede usar para manipular acordes.


<div data-category="chord"></div>



### Búsqueda ###
El filtro [msearch](/filter/chord) (que significa *music search* o *búsqueda musical*) puede utilizarse para buscar patrones musicales.

<div data-category="search"></div>



### Buscar y reemplazar ###
El filtro [shed](/filter/shed) puede utilizarse para buscar y reemplazar contenido en los datos de Humdrum.  "Shed" significa para "Humdrum <a target="_blank" href="https://www.gnu.org/software/sed/manual/sed.html">sed</a>" (disléxico, pero más fácil de pronunciar).


<div data-category="regular_expressions"></div>



### Contrapunto ###
El filtro [cint](/filter/cint) (que significa *composite intervals* o *intervalos compuestos*) puede utilizarse para estudiar el contrapunto.  El programa cint es una intersección de funcionalidades entre los programas mint y hint del Toolkit Humdrum, y crea módulos de contrapunto que constan de cuatro notas a dos voces, lo que a su vez genera dos intervalos armónicos y dos melódicos para cada módulo.


<div data-category="counterpoint"></div>


## Filtros de línea de comandos ##
Los filtros disponibles en VHV provienen de <a target="_blank" href="https://humlib.humdrum.org">humlib</a>. Los filtros pueden ser compilados como herramientas de línea de comandos:

{% include image.html
	file="command-line.jpg"
	alt="Uso de la línea de comandos de los filtros myank y transpose."
	caption="Uso de la línea de comandos de los filtros myank y transpose."
%}

{% include image.html
	file="vhv-filtering.jpg"
	alt="Filtrado equivalente en VHV."
	caption="Filtrado equivalente en VHV."
%}

Hay herramientas adicionales de línea de comandos en humlib que no están disponibles como filtros.  La mayoría de ellas son herramientas adicionales para el análisis de datos que no son la manipulación de datos o la generación de notación musical. Más herramientas para la línea de comandos también están disponibles en Humdrum Extras y el Humdrum Toolkit.  Consulta el repositorio <a target="_blank" href="https://github.com/humdrum-tools/humdrum-tools">humdrum-tools</a> para obtener instrucciones sobre cómo compilar y utilizar estas herramientas en la línea de comandos.




