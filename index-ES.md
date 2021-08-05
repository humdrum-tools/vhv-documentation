---
title: Verovio Humdrum Viewer
lang: en pl es
translator: Ana Cartagena Pérez
translation_date: 6 Jun 2021
author: Craig Stuart Sapp
creation_date: 3 Mar 2017
last_updated: 4 Mar 2017
tags: [getting_started]
sidebar: main_sidebar
keywords: homepage
permalink: /index-ES.html
summary:
---

## Información general

Verovio Humdrum Viewer es un editor digital de música en línea y una interfaz interactiva de representación de notación de ficheros Humdrum, situada en [http://verovio.humdrum.org](http://verovio.humdrum.org).  Ve a la página de[Inicio](/interface/getting_started) donde encontrarás un tutorial de cómo usar la interfaz de VHV o busca en las páginas de este sitio web pulsando en los títulos del menú de la barra lateral al lado izquierdo (o arriba) los cuales están organizados por temáticas: 

<style>



dl {

	margin-left: 10%;

	margin-right: 10%;



}



dd {

	margin-top: 0 !important;

}



</style>

Interfaz de usuario:
Una descripción de la interfaz de VHV y los conceptos básicos de cómo usarla. Los temas incluyen cómo [cargar ficheros MusicXML](interface/musicxml),
cómo [guardar ficheros MEI](interface/mei), la [coloración](interface/edit_modes) del texto musical y la [sintaxis visual de la validación de datos](interface/validation).


Comandos:
 Una lista de comandos del teclado del ordenador para interactuar con la interfaz de VHV.  Por ejemplo, [<span
class="keypress">alt-shift-T</span>](/commands/alt-t/#saving-the-entire-score-to-a-pdf-file)
descarga un PDF de la notación musical, [<span
class="keypress">alt-t</span>](/commands/alt-t/#saving-the-currently-displayed-page)
descarga un PDF de la notación musical visualizada en el momento y [<span
class="keypress">alt-l</span>](/commands/alt-l) colorea las notas de diferente manera en cada capa de música para la corrección.


Edición gráfica:
Una descripción de comandos de edición para alterar la notación musical gráficamente.  Las características musicales que pueden ser editadas gráficamente incluyen [tono](/graphic/pitch), [ligaduras](/graphic/slurs) y [barras](/graphic/beams).  La edición más complicada requiere la manipulación de la codificación musical en el editor de texto VHV.


Codificación de música:
Temas sobre la representación de características musicales en la sintaxis de Humdrum, así como temas avanzados en particular relacionados con las funciones de VHV.  Consulta la página de [ inicio](/humdrum/getting_started) para ver un tutorial interactivo sobre la codificación de música en el formato Humdrum.  Se puede encontrar una documentación más completa [el sitio web de documentación de Humdrum](http://www.humdrum.org).  El uso más común de VHV es editar la música importada a través de [MusicXML](/interface/musicxml) desde un editor gráfico de música más completo, pero los datos de Humdrum también pueden ser introducidos manualmente.


Repertorios:
Una descripción de los repertorios musicales en línea disponibles para su visualización en VHV.  La mayoría de los repertorios están enlazados desde Github, como [el repertorio de corales de Bach](https://github.com/craigsapp/bach-370-chorales) y [el repertorio de sonatas para piano de Mozart](https://github.com/craigsapp/mozart-piano-sonatas).
Otros repertorios se enumeran en [la introducción del repertorio](repertory).


Filtros:
Los filtros son comandos incrustados dentro de los datos musicales que modifican los datos.
Son herramientas de procesamiento de datos de Humdrum que forman parte de [humlib](https://humlib.humdrum.org).  La mayoría de las herramientas disponibles actualmente son para el procesamiento de datos, como [extract](/filter/extract), que es útil para extraer partes;  [transpose](/filter/transpose), que es útil para transponer partituras, y [myank](/filter/myank), que es útil para extraer compases de una partitura completa.  El filtro [disonante](/filter/dissonant) se utiliza para analizar las funciones de las notas disonantes en la música del Renacimiento y se utiliza como herramienta en el [Josquin Research Project](http://josquin.stanford.edu).


Opciones incrustadas:
[Esta sección](/options) de la documentación describe cómo incrustar las opciones de composición tipográfica de verovio en los datos de Humdrum para controlar los aspectos gráficos de la notación musical.  Aquí hay una [lista completa](/options/list) de los parámetros de verovio que se pueden establecer desde los datos musicales.  Algunos aspectos son controlables desde los comandos del teclado en la interfaz de VHV, como por ejemplo <span class="keypress">alt-w</span> para ampliar el espaciado de la música (aumentando la opción verovio <tt>spacingLinear</tt>), y <span class="keypress">alt-shift-W</span> para reducir el espaciado de la música.


miVHV
: Instrucciones y demos para usar [Verovio](http://www.verovio.org) y [Humdrum](http://www.humdrum.org) para tus propios proyectos.  En particular, tras editar una partitura de Humdrum en VHV, puedes usar el [plugin de notación de Humdrum](https://plugin.humdrum.org) para mostrar
la partitura en tu propio sitio web.


Mantenimiento
: Temas relacionados con la creación de páginas y el mantenimiento de este sitio web.


Índices
: Listas de páginas por categoría de etiquetas.


## Participantes


<style>



ul.brief li {

	color: #aaa;

	padding: 0 !important;

	margin: 0 !important;

}



</style>

<dl>

<dt>Craig Stuart Sapp</dt>

<dd>Creador</dd>

<dt>Alex Morgan</dt>

<dd>

<ul class="brief"> <li> algoritmos de etiquetado de disonacias en el filtro <i><a href="/filter/dissonant">disonante</a></i> </li> <li> definiciones de suspensión candencial en el filtro<i><a href="/filter/cint">cint</a></i>. </li> </ul>

</dd>

<dt>Piotr Szyngiera</dt>

<dd>

<ul class="brief">

<li> Validación de la sintaxis de Humdrum para el <a href="https://ace.c9.io">editor ace</a></li>

<li> <a href="/interface/edit_modes">Resaltado de la sintaxis de Humdrum</a> </li> 

<li> Interfaz <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers">Web Worker</a>para <a target="_blank" href="https://www.verovio.org">Verovio</a> </li> 

</ul>

</dd>

</dl>

Los no programadores pueden participar enviando [informes de errores y
solicitud de funciones](https://github.com/humdrum-tools/verovio-humdrum-viewer/issues) para
la interfaz web de VHV.  Si colocas tu propio repertorio de archivos Humdrum
en Github, se puede añadir a la [lista de repertorios](/repertory)
y vincularse a VHV.  Los informes sobre <a href="/filter">filtros</a> deben enviarse preferiblemente a <a
href="https://github.com/craigsapp/humlib/issues">humlib issues</a>,
y los informes sobre notación gráfica deben enviarse a <a
href="https://github.com/rism-ch/verovio/issues">verovio issues</a>
(si tienes dudas sobre dónde enviar los informes, envíalos a la [lista de issues de VHV](https://github.com/humdrum-tools/verovio-humdrum-viewer/issues)).
La mayoría de las páginas de este sitio web tienen botones de edición que pueden utilizarse para corregir errores tipográficos o añadir contenido, siempre que se tenga una cuenta de<a
href="https://github.com">Github</a>.

## Presentaciones


<dl>

<dt><a target="_blank" href="http://bit.ly/vhv-workshop-20191010">Cursillo de la UBC de octubre de 2019</a></dt>

<dd>Cursillo sobre Verovio Humdrum Viewer en la Universidad de British Columbia, 10 oct 2019.

</dd>

<dt><a target="_blank" href="http://bit.ly/iaml-2019">Cursillo de la IAML de julio de 2019</a></dt>

<dd>Cursillo sobre Verovio Humdrum Viewer en la Asociación Internacional de Bibliotecas Musicales (IAML) en Cracovia, Polonia, 18 de julio de 2019.

</dd>

<dt><a target="_blank" href="http://bit.ly/mec-2019-vhv">Cursillo del MEC de mayo de 2019</a></dt>

<dd>Cursillo sobre Verovio Humdrum Viewer y sus aplicaciones en la Music Encoding Conference, Viena, Austria, 29 de mayo de 2019.

</dd>

<dt><a target="_blank" href="http://bit.ly/simssa-xii-vhv">Presentación del SIMSSA en agosto de 2017</a></dt>

<dd>Presentación principal sobre Verovio Humdrum Viewer en el cursillo SIMSSA XII en la Universidad McGill, Montreal, Canadá, 7 de agosto de 2017.</dd>

<dt><a target="_blank" href="http://bit.ly/mec2017-vhv">Presentación del MEC en mayo de 2017</a></dt>

<dd>Presentación de Verovio Humdrum en la Music Encoding Conference en Tours, Francia, mayo de 2017.</dd>

</dl>




### Principales componentes del software


Estos son los tres principales componentes de software utilizados para crear el sitio web de VHV:

<dl>

<dt> <a href="http://www.verovio.org">verovio</a></dt>

<dd> Renderización de notación musical en C++ (usando MEI, con importación de datos de Humdrum y MusicXML y exportación a SVG y MIDI)</dd>

<dt> <a href="http://humlib.humdrum.org">humlib</a></dt>

<dd> Herramientas de conversión y análisis de datos musicales en C++ (usando Humdrum, con importaciones desde MusicXML y MEI y exportaciones a MEI y MIDI)</dd>

<dt> <a href="https://ace.c9.io">Ace editor</a></dt>

<dd> Editor de texto JavaScript</dd>

</dl>



## Apoyos institucionales/de proyectos


<style>



.logo {

	padding-top: 20px;

	padding-right: 20px;

}



.shadow {

	-webkit-filter: drop-shadow(3px 3px 2px rgba(0,0,0,0.2));

	drop-shadow(3px 3px 2px rgba(0,0,0,0.2));

}



</style>

<div style="margin-left: 100px">

<a class="logo" href="http://www.packhum.org"><img class="logo shadow" style="width:300px"  src="/images/phi-logo.png"></a>
<a class="logo" href="http://wiki.ccarh.org"><img class="logo shadow" style="width:300px" src="/images/ccarh-logo.png"></a>
<a class="logo" href="http://en.chopin.nifc.pl"><img class="logo shadow" style="width:350px" src="/images/nifc-logo.png"></a>
<a class="logo" href="https://simssa.ca/"><img class="logo shadow" style="width:250px" src="/images/simssa-logo.png"></a>

</div>

## Proyectos que utilizan VHV


<div style="margin-left: 100px">

<a class="logo" href="http://www.tassomusic.org"><img class="logo shadow" style="width:300px" src="/images/tmp-logo.png"></a>
<a class="logo" href="http://josquin.stanford.edu"><img class="logo shadow" style="width:419px" src="/images/jrp-logo.png"></a>

</div>

<div style="height:100px"></div>

Tras haber realizado la preparación de música en VHV, debe ser adecuada para su uso con
herramientas de análisis y tratamiento de la música, como <a target="_blank"
href="https://github.com/humdrum-tools/humdrum-tools">Humdrum
Tools</a>, y para su visualización en páginas web con el <a target="_blank"
href="https://plugin.humdrum.org">Plugin de notación Humdrum</a>.

Por ejemplo, el Josquin Research Project (JRP) utiliza tanto el
plugin de notación Humdrum para mostrar los íncipits musicales en <a target="_blank"
href="http://josquin.stanford.edu/work/?id=Jos2721">páginas de trabajo</a> así como una muestra aleatoria de la base de datos de puntuaciones del JRP que aparece en la <a target="_blank"
href="http://josquin.stanford.edu">página principal</a>. Además, algunas
herramientas de análisis se implementan de forma online a través de VHV.  Un ejemplo de esto es la herramienta <a href="/filter/dissonant">disonante</a>.  Páginas de trabajo, como <a target="_blank"
href="http://josquin.stanford.edu/work/?id=Jos2721">esta</a>, tienen un botón de herramienta de análisis con el nombre de "Disonante"
que enlaza con VHV, cargando los datos del sitio web
y haciendo el análisis de disonancia <a target="_blank"
href="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2721">dentro de VHV</a>.

Los archivos de otros sitios web pueden cargarse automáticamente en VHV
dando una URL como nombre de archivo en el parámetro CGI de *file*.  Por ejemplo, este enlace a VHV:

<a target="_blank" href="https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

inserta esta URL a los datos de Humdrum para el primer movimiento de la sonata <i>Claro de Luna</i> de Beethoven:

<a target="_blank" href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

Esta partitura forma parte de un repositorio Github de sonatas para piano de Beethoven:

<a target="_blank" href="https://github.com/craigsapp/beethoven-piano-sonatas">https://github.com/craigsapp/beethoven-piano-sonatas</a>

al que se puede acceder desde la parte inferior del menú de ayuda de la interfaz de VHV
(el icono del signo de interrogación en la esquina superior izquierda de la página de VHV).
