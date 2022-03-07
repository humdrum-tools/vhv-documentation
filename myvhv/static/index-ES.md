---
title: Creación de imágenes estáticas en el navegador
lang: en es
ref: myvhv-static
author: Craig Stuart Sapp
translator: David Rizo
vim: ts=3
creation_date: 9 Mar 2017
translation_date: 10 Aug 2021
last_updated: 9 Mar 2017
sidebar: main_sidebar
tags: [all]
verovio: "true"
keywords: graphical editing pitch
summary: "Uso sencillo del toolkit javascript de Verovio para mostrar los datos de Humdrum como notación gráfica en una página web independiente con un poco de javascript."
permalink: /myvhv/static/index-ES.html
---

<style>

iframe {
	background: #fff;
}

h2.clickable-header {
	padding-top: 0px !important;

}

p code.highlighter-rouge {
	padding: 0px;
	
}

p {
	margin-bottom: 16px;
	margin-top: 16px;

}

code {
	-moz-tab-size: 12;
	-o-tab-size: 12;
	tab-size: 12;
}

td.code {
	margin-bottom: 0px;
	padding:0px;
	padding-bottom: 0px; !important;
}

table td:first-child {
	width: 17px !important;
}

pre, code {
	width:100%;
	line-height: 20px;
}

td.numbers {
	line-height: 20px;
}

pre,code {
	border-radius: 0px;
	margin-bottom: 0px;
	margin-left: 0px;
	margin-right: 0px;
	margin-top: 0px;
	padding-bottom: 8px;
	padding-left: 3px;
	padding-right: 3px;
	padding-top: 7px;
	vertical-align: baseline;
}

td.code {
	padding:0;
	margin:0;
	border: 1px solid #ccc;
}

td.numbers {
	text-align: right;
	color: #eee;
	background: #604b30;
	line-height: 20px;
	border: 1px solid #ccc;
}

table.code {
	border-collapse: collapse;
	border-color: #aaa;
}


td > pre {
	padding-right: 0;
	padding-left: 0;
	magin-right: 0;
}


</style>

<script>

document.addEventListener("DOMContentLoaded", function() {
	generateCodeSpaces();
});

//
// Programmer:    Craig Stuart Sapp <craig@ccrma.stanford.edu>
// Creation Date: Sat Aug 13 13:46:54 CEST 2016
// Last Modified: Sat Aug 13 13:46:57 CEST 2016
// Filename:      scripts/main-common.js
// Syntax:        JavaScript 1.8.5/ECMAScript 5.1
// vim:           ts=3 hlsearch
//
// Description:   Shared functions for all pages on the VHV Demos website.
//


//////////////////////////////
//
// generateCodeSpaces --
//

function generateCodeSpaces() {
	var prec = document.querySelectorAll("pre");
	var line;
	var precx
	var newcolumn;
	for (var i=0; i<prec.length; i++) {
   	var code = prec[i].querySelector("code");

		var content = code.textContent;

		// content = content.replace(/^\s{56}/gm, "\t\t\t\t\t\t\t");
		// content = content.replace(/^\s{48}/gm, "\t\t\t\t\t\t");
		// content = content.replace(/^\s{40}/gm, "\t\t\t\t\t");
		// content = content.replace(/^\s{32}/gm, "\t\t\t\t");
		// content = content.replace(/^\s{24}/gm, "\t\t\t");
		// content = content.replace(/^\s{16}/gm, "\t\t");
		// content = content.replace(/^\s{8}/gm,  "\t");

		content = content.replace(/^\t\t\t\t\t\t\t/gm, "                     ");
		content = content.replace(/^\t\t\t\t\t\t/gm, "                  ");
		content = content.replace(/^\t\t\t\t\t/gm, "               ");
		content = content.replace(/^\t\t\t\t/gm, "            ");
		content = content.replace(/^\t\t\t/gm, "         ");
		content = content.replace(/^\t\t/gm, "      ");
		content = content.replace(/^\t/gm, "   ");

		// Have to remove the following condition because 
		// github jekyll removed the class tags from code elements.
		// if ((!code) || (!code.className) || code.className.match(/^\s*$/)) {
		//		continue;
		//	}

		code.textContent = content;

		var splitcontent = content.split(/[\r\n]/g);
		if (splitcontent.length > 20) {
			newcolumn = "";
			content = "";
			line = 1;
			for (var j=0; j<splitcontent.length - 1; j++) {
				newcolumn += '<span class="line-number-position">&#x200b;<span class="line-number">' 
								+ line++ + '</span></span><br>\n';
			}
			prectext = prec[i].outerHTML;
			var newtext = "<table class='code'><tr><td class='numbers'>" + newcolumn + "</td><td class='code'>" 
					+ prectext + "</td></tr></table>";
			prec[i].outerHTML = newtext;
		}
	}
}


</script>

## Ejemplo ##

El siguiente cuadro contiene una página web independiente que muestra un ejemplo musical.  Esta notación fue generada directamente dentro de la página web en lugar de ser cargada como un archivo de imagen separado desde el servidor. Esto se logra de la misma manera que se genera la notación musical en la página web de Verovio Humdrum Viewer: Los datos de Humdrum se almacenan dentro de la página web y son convertidos por el programa verovio javascript toolkit en una imagen SVG.  

<center>
<iframe width="350" height="250" src="http://www.humdrum.org/vhv-demos/simple/demo.html"></iframe>
<br>
<a href="http://www.humdrum.org/vhv-demos/simple/demo.html">view stand-alone demo page directly</a>
</center>

El texto HTML de la página se muestra en la siguiente sección junto con un comentario del código JavaScript utilizado para hacer la conversión y colocar la imagen SVG en la página.

Aquí están los datos de Humdrum que se almacenan dentro de la página de muestra:

```humdrum
**kern	**kern
*clefF4	*clefG2
*k[f#]	*k[f#]
*M4/4	*M4/4
=-	=-
8GL	8ddL
8AJ	8ccJ
16BLL	2.b;
16A	.
16G	.
16F#JJ	.
2G;	.
==	==
*-	*-
```

Si necesitas cambiar la notación gráfica de la página, todo lo que tienes que hacer es editar el texto del archivo Humdrum en la página, recargar la página, y la notación musical se actualizará automáticamente.  Como ejercicio, copia el contenido de la página más abajo e intente cambiar el texto de Humdrum a: 

<div id="myid"></div>
```humdrum
**kern	**kern
*clefF4	*clefG2
*k[f#]	*k[f#]
*M4/4	*M4/4
=-	=-
8GL	8ddL
8AJ	8cc@J
16BLL	2.b;
16AN	.
16GN	.
16F#JJ	.
2G;	.
==	==
*-	*-
!!!RDF**kern: @ = marked note
!!!RDF**kern: N = marked note color=green
```

Aquí está la notación resultante, creada en esta página a partir de los datos anteriores:
<br/><br/>

<div id="myhumdrum"></div>

También puedes incluso editar los datos de Humdrum inmediatamente por encima de la música para cambiar los colores o marcar las notas para cambiar su color en este ejemplo de notación (más sobre cómo se hace esto en la [siguiente sección](../dynamic)).

<script>

window.addEventListener("DOMContentLoaded", showMyHumdrum);

var vrvToolkit;

window.addEventListener("DOMContentLoaded", function() {
	var preelement = $("#myid").next("pre")[0];
	preelement.style.paddingBottom = "0";
	preelement.style.paddingTop = "0";
	var code = preelement.querySelector("code");
	code.setAttribute("contenteditable", "true");
	code.style.width = "100%";
	code.style.display = "inline-block";
	code.addEventListener("keyup", showMyHumdrum);
});

function showMyHumdrum() {
	if (!vrvToolkit) {
		return;
	}
	var preelement = $("#myid").next("pre")[0];
	var code = preelement.querySelector("code");

	var humdrum = code.textContent;
	console.log(humdrum);
	if (!humdrum) {
		return;
	}
	var location = document.querySelector("div#myhumdrum");
	if (!location) {
		return;
	}
	var options = {
		inputFormat: "auto",
		adjustPageHeight: 1,
		pageHeight: 1000,
		pageWidth: 600,
		scale: 60,
		font: "Leipzig"
	};
	var svg = vrvToolkit.renderData(humdrum, options);
	location.innerHTML = svg;
	location.style.marginTop = "-80px";
	location.style.marginLeft = "100px";
}

</script>

## Código fuente ##

Para implementar el ejemplo de la imagen estática, copia y pega el siguiente texto en un archivo HTML, y luego visualiza la página en un navegador web.

```html
<html>
<head>
<title>SimpleViewer</title>
<script src="https://verovio-script.humdrum.org/scripts/verovio-toolkit.js">
</script>
</head>
<body>

He aquí un breve ejemplo musical:

<script id="input" type="text/humdrum"> 
**kern	**kern
*clefF4	*clefG2
*k[f#]	*k[f#]
*M4/4	*M4/4
=-	=-
8GL	8ddL
8AJ	8ccJ
16BLL	2.b;
16A	.
16G	.
16F#JJ	.
2G;	.
==	==
*-	*-
</script>

<div id="output"></div>

<script>
	var vrvToolkit = new verovio.toolkit();
	var Input = document.querySelector("#input");
	var Output = document.querySelector("#output");
	document.addEventListener("DOMContentLoaded", displayNotation);

	function displayNotation() {
		if (!vrvToolkit) {
			return;
		}
		var data = Input.textContent;
		var options = {
			inputFormat: "humdrum",
			adjustPageHeight: 1,
			pageHeight: 1000,
			pageWidth:  1000,
			scale:  40,
			font: "Leipzig"
		};

		var svg = vrvToolkit.renderData(data, options);
		Output.innerHTML = svg;
	}
</script>

</body>
</html>
```

## Comentario del código ##

Esta sección ofrece una descripción detallada del funcionamiento de la página web.

### Carga e inicialización de Verovio ###

La línea 4 carga la versión del kit de herramientas de JavaScript de Verovio:

```javascript
<script src="https://verovio-script.humdrum.org/scripts/verovio-toolkit.js"></script>
```

El script se carga desde `https://verovio-script.humdrum.org`, donde está alojada la versión más reciente del script Verovio compatible con Humdrum.  También puedes descargar ese script y almacenarlo localmente en tu sitio web, o compilarlo directamente desde el [verovio source](https://github.com/rism-ch/verovio) (compila desde la rama `develop-humdrum` para la última versión compatible con Humdrum).

A continuación, en la línea 31 se inicializa la interfaz del verovio toolkit y se almacena en la variable `vrvToolkit`:

```javascript
   var vrvToolkit = new verovio.toolkit();
```

<div style="height:30px;"></div>

### Datos Humdrum ###

El archivo Humdrum se almacena en las líneas 11&ndash;26 en un elemento de script que tiene el ID `input`:

```javascript
<script id="input" type="text/humdrum"> 
**kern	**kern
*clefF4	*clefG2
*k[f#]	*k[f#]
*M4/4	*M4/4
=-	=-
8GL	8ddL
8AJ	8ccJ
16BLL	2.b;
16A	.
16G	.
16F#JJ	.
2G;	.
==	==
*-	*-
</script>
```

### Extracción de datos de la página ###

El ID del script puede ser cualquier texto, siempre que el ID coincida con la referencia del ID en la línea 32:

```javascript
	var Input = document.querySelector("#input");
```

En este caso los datos de Humdurm están ocultos ya que se almacenan en un elemento `<script>`, pero cualquier elemento, como un `div` podría utilizarse para almacenar los datos de Humdrum de forma visible en la página. 

El contenido del archivo Humdrum se extrae del elemento de almacenamiento en la línea 37 utilizando `textContent`:

```javascript
	var data = Input.textContent;
```

### Opciones ###

Las opciones para el kit de herramientas de Verovio se pueden encontrar en la página [verovio.org/command-line.xhtml](http://www.verovio.org/command-line.xhtml). Estas opciones son para la línea de comandos, por lo que al utilizarlas en datos JSON para la versión JavaScript del kit de herramientas Verovio, cambia los espacios por las mayúsculas.  Por ejemplo `--page-height` se convierte en `pageHeight`.

El `adjustPageHeight` se puede utilizar para mantener toda la música en una sola imagen estableciendo el `pageHeight` a un valor muy grande.  Si `adjustPageHeight` está activado, Verovio reducirá la imagen SVG para eliminar el espacio en blanco en la parte inferior de la página.  Si se establece `adjustPageHeight` a `0` o no se establece explícitamente la opción, se producirá una imagen de altura fija, posiblemente con una región en blanco después de que la música haya terminado.

El motor de grabado musical digital [Verovio](http://www.verovio.org) contiene tres fuentes posibles para elegir: `Leipzig`, `Bravura` y `Granville`.

### Generación de la imagen SVG ###

La línea 46 contiene el código que convierte los datos de Humdrum en una imagen SVG:

```javascript
      var svg = vrvToolkit.renderData(data, options);
```

La función `vrvToolkit.renderData()` toma dos parámetros: (1) los datos musicales, y (2) un objeto javascript que contiene las opciones de renderización. La salida de renderData es una imagen SVG.   Esta imagen se coloca en la página web en la línea 47:

```javascript
		Output.innerHTML = svg;
```

<div style="height:100px;"></div>


