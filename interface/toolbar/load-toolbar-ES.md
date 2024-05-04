
<div style="padding-bottom:8px;" class="toolbar" id="toolbar-3">

	<span class="nav-icon no-highlight" style="font-style: italic">Cargar</span>

	<span id="load-1" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">1</strong></span>

	<span id="load-2" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">2</strong></span>

	<span id="load-3" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">3</strong></span>

	<span id="load-4" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">4</strong></span>

	<span id="load-5" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">5</strong></span>

	<span id="load-6" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">6</strong></span>

	<span id="load-7" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">7</strong></span>

	<span id="load-8" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">8</strong></span>

	<span id="load-9" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">9</strong></span>

	<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>

</div>


<br>

La barra de herramientas de carga está estructurada de manera similar a la barra de herramientas de
guardar: al hacer clic en un botón numerado se cargará el contenido
del buffer en el editor de texto.  Los buffers que tienen contenido están resaltados en verde.  La barra de herramientas de la demostración anterior tiene contenidos en los buffers
3, 5, 7 y 8 que están disponibles para cargar en el editor de texto.
Intentar cargar un buffer vacío no tendrá ningún efecto (utiliza la función <span
class="keypress">alt-e</span> para borrar el contenido del editor de texto).  Ver el título del contenido (si lo hay) como información de las herramientas en el botón.


Los atajos de teclado permiten cargar desde los buffers sin necesidad de
ver o hacer clic en la barra de herramientas de carga de buffers.  Primero escribe el número del buffer que quieres cargar (<span class="keypress">1</span> hasta <span
class="keypress">9</span>) y luego presiona <span
class="keypress">alt-shift-R</span> (que significa "Restaurar") para cargar ese buffer en particular.  También hay un buffer especial llamado <span
class="keypress">0</span> que guarda el contenido actual del buffer automáticamente una vez por minuto.  Para recuperar el contenido
de este buffer, escribe <span class="keypress">0+alt-shift-R</span>.
Normalmente <span class="keypress">control-z</span> cumple una función similar
para deshacer los cambios en el texto.
