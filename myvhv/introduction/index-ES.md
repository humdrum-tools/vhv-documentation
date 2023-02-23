---
title: myVHV introduction
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: myvhv-introduction
sidebar: main_sidebar
tags: [all]
verovio: "true"
vim: ts=3 ft=html
keywords: verovio humdrum
summary: La sección myVHV de la documentación demuestra cómo se puede utilizar la tecnología VHV en tus propias páginas web.
permalink: /myvhv/introduction/index-ESs.html
---

<style>
table td:first-child { width: 180px; }
td, tr, table { border: none !important; }
pre#myhumdrum, pre#myhumdrum2 { background: white; }
div #myhumdrum, div #myhumdrum2 { height: 420px; overflow: auto; white-space: pre; }
</style>

[Verovio Humdrum Viewer](http://verovio.humdrum.org) es un frontend bastante complejo para el [verovio javascript toolkit](http://www.verovio.org), pero las interacciones más simples con verovio son fáciles de implementar.   Verovio es una librería de renderización de partituras musicales [escrita en C++](https://github.com/rism-ch/verovio/tree/develop-humdrum) que convierte los datos musicales de Humdrum, MEI, MusicXML o Plaine & Easie en imágenes de notación SVG, ya sea dentro de un navegador con la implementación del kit de herramientas JavaScript o en un sistema operativo en la línea de comandos. Esta sección de la documentación de VHV da ejemplos de cómo utilizar Verovio en tus propias páginas web o para generar notación musical gráfica para diversos fines.


## Uso de la línea de comandos ##

Verovio puede ser compilado para su uso en un shell de terminal de estilo unix. Este es el comando básico de Verovio para generar una imagen SVG a partir de un archivo Humdrum:

```bash
verovio file.krn
```
Esto creará un archivo llamado `file.svg` con la notación musical gráfica representada en el archivo Humdrum `file.krn`, utilizando la configuración por defecto.

### Imágenes estáticas generadas por el servidor ###

Existen varias opciones de línea de comandos que pueden utilizarse para controlar el formato de la imagen SVG generada.  Para la siguiente imagen SVG de ejemplo, se utilizaron estas opciones:

```bash
verovio input.krn --adjust-page-height -h 2000 -w 1550 --spacing-staff 3 --spacing-system 3 -s 30
```

--adjust-page-height
: reduce la altura de la imagen SVG a la altura de la música impresa (elimine cualquier espacio en blanco debajo de la música).

-h 2000
: establecerla altura de la página SVG a 2000 píxeles.

-w 1550
: establece la anchura de la página SVG en 1550 píxeles.

--spacing-staff 3
: añade a la parte inferior de cada pentagrama con 3 tonos diatónicos de espacio adicional.

--spacing-system 3
: añade en la parte inferior de cada sistema con 3 tonos diatónicos de espacio adicional.

-s 30
: escala la música al 30% del tamaño completo.

Se pueden encontrar opciones adicionales en el 
[verovio command-line page](http://www.verovio.org/command-line.xhtml).

La imagen SVG resultante se muestra a la derecha, con los datos de entrada de Humdrum mostrados al lado:

<center>
<table style="border: none; background-color: transparent">
<tr valign="top" style="background-color: transparent">
<td>
<div>
<pre style="width:150px; margin-top:25px; height:345px;" readonly id="myhumdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8GL
8E-)
(8BBn
8CJ)
4AA-
=2
(8cL
8A-)
(8En
8FJ)
4BBn
=3
(8dL
8A-)
(8En
8FJ)
(8GGL
8GJ)
=4
(8FL
8E-)
(8BBn
8CJ)
4CC
=5
(8CL
8E-
8A-)
(8G
8d-X
8cJ)
=6
(8DL
8F
8B-)
(8A-
8c
8B-J)
=7
(8A-L
8G)
(8D
8E-)
(8BB-
8DJ)
=8
2.EE-
=9:|!|:
(8B-L
8G)
(8D
8E-J)
4DD-X
=10
(8B-L
8G)
(8En
8FJ)
4GG
=11
(8d-XL
8B-)
(8En
8FJ)
8CCL
8cJ
=12
(8B-L
8A-)
(8En
8FJ)
4FF
=13
(8EE-L
8C
8F)
(8E-
8B-
8AnJ)
=14
(8DDL
8D
8G)
(8F
8c
8BnJ)
=15
(8cL
8A-)
(8F#X
8G)
8BBn
8CJ
=16
(8GGL
8D)
(8G
8F#X)
8c
8BnJ
=17
(8e-L
8c)
(8F#X
8GJ)
8AAnL
8e-J
=18
(8dL
8A-X)
(8En
8FJ)
8BBnL
8GJ
=19
(8FL
8E-
8BBn
8CJ)
(8GGL
8BnJ)
=20
(8CCL
8GG
8F
8E-J
4c)
=:|!
*-
</pre>
</div>

</td>
<td>
<div style="margin-top: -30px">
<img style="width:465px;" src="bwv1011-sarabande.svg"/>
</div>
</td>
</tr>
</table>
</center>


Consulta la página [myVHV command-line page](../command_line) para obtener más información sobre el uso de la línea de comandos de Verovio con archivos Humdrum.


## Uso de JavaScript ##

Además de poder ejecutar el conversor en la línea de comandos, Verovio también está disponible como un conjunto de herramientas javascript que permite generar imágenes SVG directamente dentro de una página web.  

### Imágenes estáticas generadas por el navegador ###

Los siguientes datos de Humdrum se utilizan para crear la notación musical de la derecha sin necesidad de almacenar la notación en un archivo de imagen cargado por separado:

<center>
<table style="padding:0 !important; border: none; background-color: transparent;">
<tr valign="top" style="background-color: transparent; padding:0 !important;">
<td style="padding:0 !important;">
<div>
<pre style="width:150px; margin-top:30px; height:345px;" readonly id="myhumdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8GL
8E-)
(8BBn
8CJ)
4AA-
=2
(8cL
8A-)
(8En
8FJ)
4BBn
=3
(8dL
8A-)
(8En
8FJ)
(8GGL
8GJ)
=4
(8FL
8E-)
(8BBn
8CJ)
4CC
=5
(8CL
8E-
8A-)
(8G
8d-X
8cJ)
=6
(8DL
8F
8B-)
(8A-
8c
8B-J)
=7
(8A-L
8G)
(8D
8E-)
(8BB-
8DJ)
=8
2.EE-
=9:|!|:
(8B-L
8G)
(8D
8E-J)
4DD-X
=10
(8B-L
8G)
(8En
8FJ)
4GG
=11
(8d-XL
8B-)
(8En
8FJ)
8CCL
8cJ
=12
(8B-L
8A-)
(8En
8FJ)
4FF
=13
(8EE-L
8C
8F)
(8E-
8B-
8AnJ)
=14
(8DDL
8D
8G)
(8F
8c
8BnJ)
=15
(8cL
8A-)
(8F#X
8G)
8BBn
8CJ
=16
(8GGL
8D)
(8G
8F#X)
8c
8BnJ
=17
(8e-L
8c)
(8F#X
8GJ)
8AAnL
8e-J
=18
(8dL
8A-X)
(8En
8FJ)
8BBnL
8GJ
=19
(8FL
8E-
8BBn
8CJ)
(8GGL
8BnJ)
=20
(8CCL
8GG
8F
8E-J
4c)
=:|!
*-
</pre>
</div>

</td>
<td>
<div style="margin-top:-20px;" id="mynotation">
</div>
</td>
</tr>
</table>
</center>

<script>

var vrvToolkit;

window.addEventListener("DOMContentLoaded", showMyHumdrum);

var options = {
	inputFormat: "humdrum",
	adjustPageHeight: 1,
	pageHeight: 2000,
	pageWidth: 1550,
	scale: 30,
	spacingSystem: 3,
	spacingStaff: 3,
	font: "Leipzig"
};

function showMyHumdrum() {
	vrvToolkit = new verovio.toolkit();
	var myhumdrum = document.querySelector("#myhumdrum");
	if (!myhumdrum) {
		return;
	}
	var location = document.querySelector("#mynotation");
	if (!location) {
		return;
	}

	var svg = vrvToolkit.renderData(myhumdrum.textContent, options);
	location.innerHTML = svg;
	location.style.marginLeft = "20px";
}


</script>

Para saber cómo generar imágenes SVG estáticas dentro de una página web, consulta [esta página](../static).


### Imágenes dinámicas generadas por el navegador ###

Usar Verovio para crear imágenes estáticas en páginas web está bien, pero no es muy diferente de generar las imágenes en la línea de comandos y cargarlas como una imagen desde el servidor web.  Aquí está la misma música que en el ejemplo anterior, pero ahora puedes editar los datos de Humdrum y la notación de la derecha se actualizará inmediatamente reconvirtiendo los datos de Humdrum cambiados en una nueva imagen SVG.

{% include verovio.html
	source="dynamic_humdrum"
	pageHeight="2000"
	pageWidth="1550"
	scale="30"
%}
<script  type="text/humdrum" id="dynamic_humdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8GL
8E-)
(8BBn
8CJ)
4AA-
=2
(8cL
8A-)
(8En
8FJ)
4BBn
=3
(8dL
8A-)
(8En
8FJ)
(8GGL
8GJ)
=4
(8FL
8E-)
(8BBn
8CJ)
4CC
=5
(8CL
8E-
8A-)
(8G
8d-X
8cJ)
=6
(8DL
8F
8B-)
(8A-
8c
8B-J)
=7
(8A-L
8G)
(8D
8E-)
(8BB-
8DJ)
=8
2.EE-
=9:|!|:
(8B-L
8G)
(8D
8E-J)
4DD-X
=10
(8B-L
8G)
(8En
8FJ)
4GG
=11
(8d-XL
8B-)
(8En
8FJ)
8CCL
8cJ
=12
(8B-L
8A-)
(8En
8FJ)
4FF
=13
(8EE-L
8C
8F)
(8E-
8B-
8AnJ)
=14
(8DDL
8D
8G)
(8F
8c
8BnJ)
=15
(8cL
8A-)
(8F#X
8G)
8BBn
8CJ
=16
(8GGL
8D)
(8G
8F#X)
8c
8BnJ
=17
(8e-L
8c)
(8F#X
8GJ)
8AAnL
8e-J
=18
(8dL
8A-X)
(8En
8FJ)
8BBnL
8GJ
=19
(8FL
8E-
8BBn
8CJ)
(8GGL
8BnJ)
=20
(8CCL
8GG
8F
8E-J
4c)
=:|!
*-
</script>


Prueba a cambiar los datos de Humdrum en el ejemplo anterior, por ejemplo, eliminando la armadura de clave, cambiando a clave de tenor (`*clefC4`), o cambiando algunas alturas de nota.  La imagen SVG de la derecha debería actualizarse a medida que realices los cambios.



