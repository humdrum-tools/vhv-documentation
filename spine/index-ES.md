---
title: Tipos de columnas entendidos por VHV
lang: en es
ref: data types
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 2 Sep 2019
translation_date: 10 Aug 2021
last_updated: 2 Sep 2019
tags: [all]
sidebar: main_sidebar
keywords: data types
vim: ts=3 ft=javascript
summary: "Tipos de columnas entendidos por Verovio Humdrum Viewer."
permalink: /spine/index-ES.html
---
Esta sección de la documentación de VHV describe los tipos de datos que conoce VHV y que se utilizan para convertir los datos de Humdrum en notación musical.

Los tipos de datos, o <i>interpretaciones exclusivas</i> en la terminología de Humdrum, aparecen al principio de una columna de datos y van precedidos de dos asteriscos (`**`).  Los datos de ese tipo pueden darse entonces en la columna asignada a ese tipo de datos y el terminador de la columna (`*-`) termina la columna iniciada con la interpretación exclusiva inicial.

Aquí hay una lista de las interpretaciones exclusivas que son procesadas por Verovio Humdrum Viewer cuando convierte los datos de Humdrum en notación musical:

<style>
table.exinterp td {
	text-align: top;
}
</style>

Tipos de columnas musicqles:

Estos tipos de datos están cubiertos en la sección [Music encoding](/humdrum/getting_started) de la documentación.

<table class="exinterp">

<tr>
	<td>
		<tt>**dynam</tt>
	</td>
	<td>
		Este tipo de datos describe la dinámica asociada a uno o más <tt>**kern</tt> de columna que se encuentran a la izquierda de este tipo de columna.
	</td>
</tr>

<tr>
	<td>
		<tt>**kern</tt>
	</td>
	<td>
		Se trata del tipo de datos de representación musical "central", que describe, en particular, los tonos y las duraciones de las notas, así como otros elementos musicales, como las ligaduras y las articulaciones.
	</td>
</tr>

<tr>
	<td>
		<tt>**text</tt>
	</td>
	<td>
		Este tipo de datos describe el texto de la letra que se mostrará con la música.  Cada columna de datos de texto se asignará a un verso diferente en la pantalla de notación.
	</td>
</tr>

<tr>
	<td>
		<tt>**fb</tt>
	</td>
	<td>
		Este es el tipo de datos que describe la base de figura para mostrar con la columna de kern en el lado izquierdo de la columna (o si la columna <tt>**fb</tt> no tiene columna de kern después de ella, los símbolos de bajo cifrado se muestran debajo del sistema en lugar de asociarse con una parte específica.
	</td>
</tr>

<tr>
	<td>
		<tt>**recip</tt>
	</td>
	<td>
		Este tipo de datos funciona de forma similar a una columna `**kern` cuando se analiza el ritmo de los datos de Humdrum, pero la columna no genera un pentagrama musical cuando la partitura se representa en notación gráfica.
	</td>
</tr>

</table>

Tipos de datos gráficos:

Estos tipos de datos se utilizan para mostrar otros tipos de datos de información exclusiva como datos de texto de acordes o letras en la notación musical. Cualquier tipo de datos puede mostrarse como si fuera texto en la notación musical, ya sea tratado como letra (versos) o como acordes.  La forma más sencilla de mostrar estos datos sería cambiar el tipo de datos de la columna por uno de los siguientes tipos, o posponer el tipo de datos original a uno de los siguientes nombres de metatipos de datos, de forma que el tipo de datos de la columna quede incrustado como una etiqueta de clase en la imagen SVG resultante.


<table class="exinterp">

<tr>
	<td>
		<tt><a href="/spine/vdata">**vdata</a></tt>
	</td>
	<td>
		Este tipo de datos se muestra como letra de la música.  La principal diferencia es que los espacios en los datos de <tt>**text</tt> generarán marcadores de elisión, mientras que los espacios en las columnas de <tt>**vdata</tt> se conservarán como espacios. Al igual que los datos de <tt>**text</tt>, los datos de <tt>**vdata</tt> deben coincidir con las notas del pentagrama asociado debido a las limitaciones impuestas a la letra por el formato MEI utilizado para crear la notación gráfica en VHV. 	Por otra parte, <tt>**vdata</tt> no puede adjuntarse a los silencios.
	</td>
</tr>

<tr>
	<td>
		<tt><a href="/spine/cdata">**cdata</a></tt>
	</td>
	<td>
		El tipo de datos <tt>**cdata</tt> es similar a <tt>**vdata</tt>, pero se muestra sobre los pentagramas por defecto, y no tiene que estar asociado a una nota en el pentagrama emparejado. 
	</td>
</tr>

<tr>
	<td>
		<tt><a href="/spine/vvdata">**vvdata</a></tt>
	</td>
	<td>
		El tipo de datos <tt>**vvdata</tt> está relacionado con <tt>**vdata</tt>, pero en lugar de generar cada "verso" con una columna separada, los versos se generan por espacios dentro de los datos vvdata.
	</td>
</tr>

<tr>
	<td>
		<tt><a href="/spine/ccdata">**ccdata</a></tt>
	</td>
	<td>
		Probablemente aún no existe, pero será similar a <tt>vvdata</tt> como compañero del tipo de datos <tt>**cdata</tt>.
	</td>
</tr>

<tr>
	<td>
		<tt><a href="/spine/color">**color</a></tt>
	</td>
	<td>
		Se utiliza para colorear las notas por pentagrama o sistema.
	</td>
</tr>


</table>





