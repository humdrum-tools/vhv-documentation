

<div class="toolbar" id="toolbar-6">
	<input id="scriptid"  type="text" spellcheck="false" placeholder="ID de la secuencia de comandos de la hoja de cálculo">
	<div title="Cargar los datos en la hoja de cálculo" onclick="uploadDataToSpreadsheet()" class='nav-icon fa fa-cloud-upload'></div>
	<div title="Descargar los datos de la hoja de cálculo" class='nav-icon fa fa-cloud-download'></div>
	<div title="Abrir la hoja de cálculo vinculada" class='nav-icon fa fa-file-text'></div>
	<div title="Sobre las hojas de cálculo" onclick="showSpreadsheetHelp()" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon" onclick="gotoNextToolbar(6, event)">
		<div title="Ir al siguiente menú de herramientas (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br><br>

La barra de herramientas de la hoja de cálculo permite la comunicación bidireccional entre
VHV y Google Sheets.  Esto es especialmente útil para editar
partituras orquestales, ya que la línea de la etiqueta del instrumento se puede congelar
en la parte superior de la hoja mientras se edita más abajo en la partitura.

<br><br>

<table class="toolbar-info">

<tr><td>
<div style="font-size:3rem !important;" class="toolbar">
	<span id="search-group">
		<input id="scriptid2" type="text" autocomplete="off" spellcheck="false" placeholder="ID de la secuencia de comandos">
	</span>
</div>
</td>
<td>

    <span class="summary-icon">Identificación de la secuencia de comandos de la hoja de cálculo.</span>
    
    Consulta la <a target="spreadsheet" href="spreadsheet"> página de documentación sobre la interacción con la hoja de cálculo</a>
    para saber cómo crear una secuencia de comandos (script) y obtener su ID para pegarlo en este cuadro con el fin de
    conectarse a una hoja de cálculo en particular.

</td>
</tr>


<tr><td>
<div class="toolbar">
	<div title="Cargar el contenido del editor en la hoja de cálculo" class='nav-icon fa fa-cloud-upload'></div>
</div>
</td>
<td>

    <span class="summary-icon">Subir a la hoja de cálculo.</span>
    
    El contenido del editor de texto sustituirá el contenido actual
    de la hoja de cálculo vinculada.  Mantén pulsada la tecla de mayúsculas cuando hagas clic en este icono
    para evitar el filtro del tabulador, que también permite cargar datos Humdrum no válidos
    (que podrían ser más fáciles de arreglar en la hoja de cálculo).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Descargar el contenido de la hoja de cálculo al editor" class='nav-icon fa fa-cloud-download'></div>
</div>
</td>
<td>

    <span class="summary-icon">Descargar de la hoja de cálculo.</span>
    
    El contenido de la hoja de cálculo vinculada sustituirá el contenido actual
    del editor de texto VHV.  Mantén pulsada la tecla de mayúsculas cuando hagas clic en este icono
    para evitar el filtro del tabulador, que también permite descargar datos no válidos
    (que podrían ser más fáciles de arreglar en el editor de texto).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Abrir la hoja de cálculo vinculada" class='nav-icon fa fa-file-text'></div>
</div>
</td>
<td>

    <span class="summary-icon">Abrir hoja de cálculo vinculada.</span>
    
    El ID de la hoja de cálculo puede añadirse al ID de la secuencia de comandos en el
    cuadro de texto de entrada, separándolos con una barra vertical (|)
    o un espacio.  Cuando hay un ID de hoja de cálculo, este icono
    aparecerá, y puedes hacer clic en él para abrir la hoja de cálculo
    en otra pestaña.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Sobre la barra de herramientas" class='nav-icon fa fa-question-circle'></div>
</div>
</td>
<td>

    <span class="summary-icon"><a href="spreadsheet">Documentación de la barra de herramientas de la hoja de cálculo.</a></span>

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
    
    Para volver a esta barra de herramientas directamente, pulsa <span class="keypress">6+alt-n</span>.

</td>
</tr>

</table>


<br><br>
Consulta la página de [documentación para la interacción con la hoja de cálculo](spreadsheet) para
obtener información sobre cómo configurar la interacción con la hoja de cálculo y utilizar el sistema.



