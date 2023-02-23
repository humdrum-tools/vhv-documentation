---
title: Edit modes and syntax highlighting
lang: en es
page_language: es
translator: David Rizo
translation_date: 5 Aug 2021
translation_update:
ref: interface-edit_modes
tags: [all, getting_started]
keywords: interface color colorize coloring syntax highlighting
summary: "A Description of the two editing modes in VHV, and Humdrum syntax coloring."
sidebar: main_sidebar
permalink: /interface/edit_modes/index-ES.html
---
La edición de texto en [Verovio Humdrum Viewer](http://verovio.humdrum.org) utiliza el editor
[ace](https://ace.c9.io/).  Hay dos modos en los que los
contenidos pueden ser editados: 
(1) el editor de texto simple inicial 
(2) un editor vi útil para las personas que conocen [vi/vim](http://www.openvim.com/).
Cambia entre estos dos modos pulsando <span class="keypress">alt-v</span>.


## Modo de texto plano ##
El modo de edición de texto plano se indica con un fondo claro, que coincide con el 
color de fondo del área de notación de la página:

{% include image.html
	file="colorize-light.png"
	max-width="100%"
	alt="light-themed colorizing"
	caption="Tema claro para el modo de texto plano."
%}

Al editar los archivos de Humdrum, su contenido será coloreado por la función sintáctica:

<style>
.light.colorlist tr,
.light.colorlist td,
.light tbody tr:nth-of-type(even),
.light tbody tr:nth-of-type(odd),
.light th,
.light tr,
.light td {
	background: #fdf6e3 !important;
}
.light td, .light th {
	color: black;
}

.colorlist td > div,
.colorlist td  {
	width: 80px;
}
</style>



<table style="width:100%" class="double">
<tr><td>
<table style="width:100%; padding:0; margin:0;" class="light colorlist">
<tr><th><div>ejemplo</div></th><th>significado</th></tr>
<tr><td><div style="color:red">**kern</div></td><td>interpretaciones&nbsp;exclusivas</td></tr>
<tr><td><div style="color:magenta">*^</div></td><td>manipuladores de <em>spine</em></td></tr>
<tr><td><div style="color:darkviolet">*M4/4</div></td><td>interpretaciones <em>tandem</em></td></tr>
<tr><td><div style="color:darkviolet; background: rgba(75,0,130,0.3)">*&gt;A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div></td><td>etiquetas de sección</td></tr>
<tr><td><div style="color:green">!!!OTL:</div></td><td>registros de referencia</td></tr>
<tr><td><div style="color:blue">!! comment</div></td><td>comentarios globales</td></tr>
<tr><td><div style="color:#2fc584">!bass</div></td><td>comentarios locales</td></tr>
</table>
</td><td>
<table style="width:100%; padding:0; margin:0;" class="light colorlist">
<tr><th><div>ejemplo</div></th><th>significado</th></tr>
<tr><td><div style="color:orange">!LO:N:vis=0</div></td><td>comandos de diseño</td></tr>
<tr><td><div style="color:limegreen">!!!filter:&nbsp;autobeam</div></td><td>filtros</td></tr>
<tr><td><div style="color:olive">!!!Xfilter:&nbsp;autobeam</div></td><td>filtros usados</td></tr>
<tr><td><div style="color:gray; background:rgba(0, 0, 0, 0.06);">=2</div></td><td>barrados</td></tr>
<tr><td><div style="color:gray">.</div></td><td><em>tokens null</em></td></tr>
<tr><td><div style="color:black">4E</div></td><td><em>tokens</em> de datos</td></tr>
<tr><td><div style="background:#EEf3D5">&nbsp;&nbsp;&nbsp;</div></td><td>línea del cursor activa</td></tr>
</table>
</td></tr>
</table>


## modo vi ##

{% include image.html
	file="colorize-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Coloración del tema oscuro para el modo vi (<span class='keypress'>alt-v</span>)."
%}


Coloreado por sintaxis en modo vi:

<style>
.dark.colorlist tr,
.dark.colorlist td,
.dark tbody tr:nth-of-type(even),
.dark tbody tr:nth-of-type(odd),
.dark tr,
.dark th,
.dark td {
	background: #002b36 !important;
}
.dark td, .dark th {
	color: white;
}
table.colorlist tr td, table.colorlist td {
	hyphens: none;
}
</style>

<table style="width:100%" class="double">
<tr><td>
<table style="width:100%; padding:0; margin:0;" class="colorlist dark">
<tr><th><div>ejemplo</div></th><th>significado</th></tr>
<tr><td><div style="color:red">**kern</div></td><td>interpretaciones&nbsp;exclusivas</td></tr>
<tr><td><div style="color:magenta">*^</div></td><td>manipuladores de <em>spine</em></td></tr>
<tr><td><div style="color:darkviolet">*M4/4</div></td><td>interpretaciones tandem</td></tr>
<tr><td><div style="color:darkviolet; background: rgba(255,200,255,0.6)">*&gt;A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div></td><td>etiquetas de sección</td></tr>
<tr><td><div style="color:green">!!!OTL:</div></td><td>registros de referencia</td></tr>
<tr><td><div style="color:lightblue">!! comment</div></td><td>comentarios globales</td></tr>
<tr><td><div style="color:#2fc584">!bass</div></td><td>comentarios locales</td></tr>
</table>
</td><td>
<table style="width:100%; padding:0; margin:0;" class="colorlist dark">
<tr><th><div>ejemplo</div></th><th>significado</th></tr>
<tr><td><div style="color:orange">!LO:N:vis=0</div></td><td>comandos de diseño</td></tr>
<tr><td><div style="color:chartreuse">!!!filter:&nbsp;autobeam</div></td><td>filtros</td></tr>
<tr><td><div style="color:olive">!!!Xfilter:&nbsp;autobeam</div></td><td>filtros usados</td></tr>
<tr><td><div style="color:gray; background:#1f454e;">=2</div></td><td>barlines</td></tr>
<tr><td><div style="color:gray">.</div></td><td>><em>tokens null</em></td></tr>
<tr><td><div style="color:white">4E</div></td><td><em>tokens</em> de datos</td></tr>
<tr><td><div style="color:white; background:#194a40">&nbsp;&nbsp;&nbsp;  </div></td><td>línea del cursor activa</td></tr>
</table>
</td></tr>
</table>

## Resaltado de errores de sintaxis básicos ##

### Errores de sintaxis por tabulador ###
Los tabuladores no pueden empezar una línea, ni terminar una línea, ni aparecer más de una vez entre los tokens en la sintaxis Humdrum 
de la sintaxis.  Cualquiera de estos casos no válidos se resalta en rojo:

<style>
table.double {
	width: 100%;
	border: none !important;
	max-width: 100%;
}
.double td {
	width: 50% !important;
}
.double tr, .double td, .double tbody tr:nth-of-type(odd) {
	background: none !important;
}
.double tbody tr td {
	border: none !important;
}
</style>

<table class="double"><tr><td>

{% include image.html
	file="taberror-light.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Errores de tabulación en el tema de texto plano."
%}

</td><td>

{% include image.html
	file="taberror-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Errores de tabulación en el tema vi."
%}


</td></tr></table>


### Advertencias sobre la sintaxis en el uso de espacios ###
Por lo general, los tokens no comienzan ni terminan con caracteres de espacio, y los sub-tokens múltiples  se separan con un solo espacio (en formatos de datos como `**kern`).  Cuando un token empiezao termina con un espacio, o hay más de un espacio entre subtokens, el espacio se resaltará
en azul.  Por lo general, se trata de un error de sintaxis que debe corregirse.


<table class="double"><tr><td>

{% include image.html
	file="spacewarning-light.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Advertencias de espacio en el tema de texto plano."
%}

</td><td>

{% include image.html
	file="spacewarning-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Avisos de espacio en el tema vi."
%}


</td></tr></table>


## Ficheros de sintaxis ##
Aquí están los archivos de análisis y resaltado de sintaxis de Humdrum para el editor Ace:

* [mode-humdrum.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/tree/master/scripts/ace/mode-humdrum.js): archivo de análisis sintáctico
* [theme-humdrum_light.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/tree/master/scripts/ace/theme-humdrum_light.js) tema de resaltado de color claro
* [theme-humdrum_dark.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/tree/master/scripts/ace/theme-humdrum_dark.js) tema de resaltado de color oscuro


