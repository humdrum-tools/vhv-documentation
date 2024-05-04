
<div style="padding-bottom:8px;" class="toolbar" id="toolbar-2">

	<span class="nav-icon no-highlight" style="font-style: italic">Guardar</span>

	<span id="save-1" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">1</strong></span>

	<span id="save-2" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">2</strong></span>

	<span id="save-3" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">3</strong></span>

	<span id="save-4" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">4</strong></span>

	<span id="save-5" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">5</strong></span>

	<span id="save-6" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">6</strong></span>

	<span id="save-7" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">7</strong></span>

	<span id="save-8" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">8</strong></span>

	<span id="save-9" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">9</strong></span>

	<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>

</div>

<br>

La barra de herramientas para guardar se utiliza para guardar el contenido actual del editor de textos en uno de los nueve buffers del buscador web.   Estos buffers pueden volver a ponerse dentro del editor de texto desde el siguiente menú de la barra de herramientas (<span class="keypress">alt-n</span> te lleva al siguiente menú, o haz clic en el botón redondo de la barra de herramientas para ir a la barra de herramientas de carga).

Cuando un buffer tiene contenido, su correspondiente botón de guardar se resaltará en rojo.  Esto se demuestra en la barra de herramientas del ejemplo
de arriba, donde los botones para los buffers 3, 5, 7 y 8 se llenan con algunos contenidos.  Esto es útil para saber qué buffers tienen
contenidos, así como para evitar que se borren accidentalmente
contenidos previamente almacenados.  Si quieres borrar el contenido de
un buffer, guarda el contenido del editor de texto cuando este esté vacío, o haz <span class="keypress">shift+clic</span> sobre el icono del buffer
para borrar también su contenido.

La información sobre los buffers llenos pone el título a los datos cuando han sido
almacenados.  La información sobre la herramienta coincide con la descripción dada en la parte superior de la página de
la página VHV, y suele ser el compositor y el título, procedentes de
los registros de referencia <code class="mine">!!!COM:</code> <code class="mine">!!!OTL:</code>; sin embargo, un formato diferente para la descripción
en la parte superior de la página (y para esta información sobre herramientas) puede hacerse utilizando el
registro de referencia <code class="mine">!!!title:</code>.

Los atajos de teclado permiten guardar en los buffers sin necesidad de ver
o hacer clic en la barra de herramientas para guardar en el buffer.  Primero escribe el número del
buffer que quieres guardar (<span class="keypress">1</span>
hasta
<span class="keypress">9</span>) y luego pulsa
<span class="keypress">alt-shift-S</span> para guardar en ese buffer concreto.
