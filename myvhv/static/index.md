---
title: Creating static in-browser images
lang: en
author: Craig Stuart Sapp
vim: ts=3
creation_date: 9 Mar 2017
last_updated: 9 Mar 2017
sidebar: main_sidebar
tags: [all]
verovio: "true"
keywords: graphical editing pitch
summary: "Simple use of the verovio javascript toolkit to display Humdrum data as graphical notation on a stand-alone webpage with a tiny bit of javascript."
permalink: /myvhv/static/index.html
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

## Example ##

The following box contains an indepndent webpage showing a musical
example.  This notation was generated directly within the webpage
rather than being loaded as a separate image file from the server.
This is accomplished in the same manner as music notation is generated
on the Verovio Humdrum Viewer website: Humdrum data is stored inside
the webpage and is converted by the verovio javascript toolkit
program into an SVG image.  

<center>
<iframe width="350" height="250" src="http://www.humdrum.org/vhv-demos/simple/demo.html"></iframe>
<br>
<a href="http://www.humdrum.org/vhv-demos/simple/demo.html">view stand-alone demo page directly</a>
</center>

The HTML text for the page is shown in the next section along with
a commentary of the JavaScript code used to do the conversion and
place the SVG image on the page.

Here is the Humdrum data which is stored inside of the sample page:

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

If you need to change the graphic notation on the page, all you
have to do is edit the Humdrum file text on the page, reload the
page, and the music notation will automatically be updated.  As an
exercise, copy the contents of the page further below and try
changing the Humdrum text to:


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

Here is the resulting notation, created on this page from 
the above data:
<br/><br/>

<div id="myhumdrum"></div>

Also you can even edit the Humdrum data immediately above the music
to change colors or mark notes to change their color in this notation
example
(more about how this is done in the [next section](../dynamic)).

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

## Source code ##

To implement the static image example, copy and paste the following
text into an HTML file, and then view the page in a web browser.

```html
<html>
<head>
<title>SimpleViewer</title>
<script src="http://verovio-script.humdrum.org/scripts/verovio-toolkit.js">
</script>
</head>
<body>

Here is a short musical example:

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

## Code commentary ##

This section gives a detailed description of how the webpage works.

### Loading and initializing verovio ###

Line 4 loads the JavaScript toolkit version of verovio:

```javascript
<script src="http://verovio-script.humdrum.org/scripts/verovio-toolkit.js"></script>
```

The script is loaded from `http://verovio-script.humdrum.org`, where
the most recent version of the Humdrum-aware verovio script is
hosted.  Alternatively you can download that script and store it
locally on your website, or compile directly from the [verovio
source](https://github.com/rism-ch/verovio) (compile from the
`develop-humdrum` branch for the latest Humdrum-aware version).

Next, on line 31 the verovio toolkit interface is initialized and stored in 
the `vrvToolkit` variable:

```javascript
   var vrvToolkit = new verovio.toolkit();
```

<div style="height:30px;"></div>

### Humdrum data ###

The Humdrum file is stored on lines 11&ndash;26 in a script element
having the ID `input`:

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

### Extracting Humdrum data from page ###

The ID for the script could be any text, as long as the ID
matches the ID reference on line 32:

```javascript
	var Input = document.querySelector("#input");
```

In this case the Humdurm data is hidden since it is stored
in a `<script>` element, but any element, such as a `div` could
be used to store the Humdrum data visibly on the page.

The Humdrum file contents is extracted from the storage element on line 37 
using `textContent`:

```javascript
	var data = Input.textContent;
```

### Options ###

Options for the verovio toolkit can be found on the page
[verovio.org/command-line.xhtml](http://www.verovio.org/command-line.xhtml).
These options are for the command line, so when using in JSON data
for the JavaScript version of the verovio toolkit, change spaces
into capitalization.  For example `--page-height` becomes `pageHeight`.

The `adjustPageHeight` can be used to keep all music in a single 
image by setting the `pageHeight` to a very large value.  If 
`adjustPageHeight` is enabled, verovio will shrink the SVG image to
remove blank space at the bottom of the page.  Setting `adjustPageHeight`
to `0` or not explicitly setting the option will produce a 
fixed-height image, possibly with a blank region after the 
music is finished.

The [verovio](http://www.verovio.org) typesetting engine contains 
three possible fonts to choose from: `Leipzig`, `Bravura` and `Granville`.

### Generating the SVG image ###

Line 46 contains the code that converts the Humdrum data into an
SVG image:

```javascript
      var svg = vrvToolkit.renderData(data, options);
```

The `vrvToolkit.renderData()` function takes two parameters: (1)
the musical data, and (2) a javascript object containing the 
rendering options. The output from renderData is an SVG image.  
This image is then placed on the webpage at 
line 47:

```javascript
		Output.innerHTML = svg;
```

<div style="height:100px;"></div>


