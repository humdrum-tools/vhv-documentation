

<div class="toolbar" id="toolbar-4">

	<span id="search-results" style="vertical-align: 6%; font-style: italic" class="nav-icon">búsqueda</span>

	<span id="search-group">

		<input id="search-pitch"    type="text" spellcheck="false" placeholder="tono">

		<input id="search-interval" type="text" spellcheck="false" placeholder="intervalo">

		<input id="search-rhythm"   type="text" spellcheck="false" placeholder="ritmo">

	</span>

	<div title="Buscar melódicamente la nota más alta del acorde" class='nav-icon fa fa-hand-o-up'></div>

	<div title="Mostrar solo las medidas con coincidencias" class='nav-icon fa fa-search-minus'></div>

	<div title="Ayuda para la búsqueda" class='nav-icon fas fa-question-circle'></div>

	<span id="line-break-icon">

		<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>

	</span>

</div>

<br>

La barra de búsqueda te permite localizar características musicales en la
partitura.  Escribe las características en las casillas de tono, intervalo y
ritmo en la barra de herramientas y las coincidencias se resaltarán en la partitura.  Las características pueden buscarse en conjunto, como la
secuencia de tono "cdefg" que comienza en un ritmo de "1" (nota entera).
A medida que escribes en los campos de búsqueda, el número de coincidencias se mostrará
a la izquierda de las casillas de búsqueda:

<div style="margin-left: 50px;" class="toolbar" id="toolbar-4">

	<span id="search-results" style="vertical-align: 6%; margin-bottom:5px; font-size:2.25rem; font-style: italic" class="nav-icon">5 coincidencias</span>

	<span id="search-group">

		<input id="search-pitch"    value="cefg" type="text" spellcheck="false" placeholder="tono">

		<input id="search-interval" type="text" spellcheck="false" placeholder="intervalo">

		<input id="search-rhythm"   value="1" type="text" spellcheck="false" placeholder="ritmo">

	</span>

	<div title="Buscar melódicamente la nota más alta del acorde" class='nav-icon fa fa-hand-o-up'></div>

	<div title="Mostrar solo las medidas con coincidencias" class='nav-icon fa fa-search-minus'></div>

	<div title="Ayuda para la búsqueda" class='nav-icon fas fa-question-circle'></div>

	<span id="line-break-icon">

		<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>

	</span>

</div>


<br>

<table class="toolbar-info">

<tr><td>

<div style="font-size:3rem !important;" class="toolbar">

	<span id="search-group">

		<input id="search-pitch" type="text" autocomplete="off" spellcheck="false" placeholder="tono">

	</span>

</div>

</td>

<td>

    <span class="summary-icon">Cuadro de búsqueda de clase de tono.</span>
    
    Escribe las letras de la A a la G (sin distinguir entre mayúsculas y minúsculas) para buscar
    por clase de tono.  Añade alteraciones cromáticas opcionales después del
    nombre: "n" para natural, "-" para bemol y "#" para sostenido.
    Los espacios entre las notas son opcionales.

</td>

</tr>

<tr><td>

<div style="font-size:3rem !important;" class="toolbar">

	<span id="search-group">

		<input id="search-interval" type="text" autocomplete="off" spellcheck="false" placeholder="intervalo">

	</span>

</div>

</td>

<td>

    <span class="summary-icon">Cuadro de búsqueda de intervalos.</span>
    
    Escribe los números del 1 al 9 con un signo menos opcional
    para los intervalos descendentes.  "1" significa una nota repetida, "2" es
    un paso "3" es una tercera, y así sucesivamente.  "-3" significa una tercera menor.
    Los espacios entre los intervalos son opcionales.

</td>

</tr>



<tr><td>

<div style="font-size:3rem !important;" class="toolbar">

	<span id="search-group">

		<input id="search-rhythm" type="text" autocomplete="off" spellcheck="false" placeholder="ritmo">

	</span>

</div>

</td>

<td>

    <span class="summary-icon">Caja de búsqueda de ritmos.</span>
    
    Escribe los ritmos como números, por ejemplo "1" para la nota entera, "2"
    para la media nota, "4" para la negra, etc.  Los números
    pueden ir seguidos de uno o varios puntos de aumento (".").
    Los espacios son opcionales, y las rimas como "16", "32" y "64"
    serán analizadas automáticamente.  Solo la potencia de dos ritmos
    está disponible en este tiempo.

</td>

</tr>


<tr><td>

<div class="toolbar">

	<div title="Buscar melódicamente la nota más alta del acorde" class='nav-icon fa fa-hand-o-up'></div>

<br>

	<div title="Buscar melódicamente la nota más alta del acorde" class='nav-icon fa fa-hand-o-down'></div>

</div>

</td>

<td>

    <span class="summary-icon">Buscar nota de acorde.</span>
    
    Si la música contiene acordes, elige la nota más alta (icono que apunta hacia arriba), o la nota más baja (icono que apunta hacia abajo)
    cuando busques patrones melódicos.

</td>

</tr>



<tr><td>

<div class="toolbar">

	<div title="Mostrar solo las medidas con coincidencias" class='nav-icon fa fa-search-minus'></div>

<br>

	<div title="Mostrar solo las medidas con coincidencias" class='nav-icon fa fa-search-plus'></div>

</div>

</td>

<td>

    <span class="summary-icon">Vista de resultados comprimida/ampliada.</span>
    
    Este botón controla la visualización de los resultados de la búsqueda:
    o bien muestra toda la puntuación, o bien muestra solo las medidas que
    contienen coincidencias.

</td>

</tr>



<tr><td>

<div class="toolbar">

	<div title="Mostrar solo las medidas con coincidencias" class='nav-icon fa fa-question-circle'></div>

</div>

</td>

<td>

    Mostrar <a href="/interface/search">más información</a> sobre la búsqueda.

</td>

</tr>



<tr><td>

<div class="toolbar">

	<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>

</div>

	<span class="keypress">alt-n</span>

	<span class="keypress">#-alt-n</span>

</td>

<td>

    <span class="summary-icon">Ir a la siguiente barra de herramientas.</span>
    
    Para volver a esta barra de herramientas directamente, pulsa <span class="keypress">4+alt-n</span>.

</td>

</tr>

</table>

<br><br>

Para obtener más información sobre la búsqueda, consulta la [página de documentación de búsqueda](/interface/search).
