---
title: Creating static in-browser images from EsAC data
lang: en es
ref: myvhv-static-esac
author: Craig Stuart Sapp
translator: David Rizo
vim: ts=3
creation_date: 10 Jun 2017
translation_date: 10 Aug 2021
last_updated: 10 Jun 2017
sidebar: main_sidebar
tags: [all]
verovio: "true"
keywords: esac notation 
summary: "Uso sencillo del conjunto de herramientas verovio javascript para mostrar los datos de EsAC como notación gráfica en una página web independiente con un poco de javascript."
permalink: /myvhv/static-esac/index-ES.html
---

<style>

/* Analytic phrase markers */

.phraseStart { fill: green; }
.phraseStart [stroke] { stroke: green; }

.phraseStop { color: blue; }
.phraseStop [stroke] { stroke: blue; }

.phraseStart.phraseStop { color: orange; }
.phraseStart.phraseStop [stroke] { stroke: orange; }

</style>



La siguiente notación musical se genera a partir de los datos de EsAC que aparecen a continuación.

<div id="notation"></div>
<pre style="width:500px; margin:auto; margin-top:50px;" id="text"></pre>

<script type="application/x-esac" id="source">!!!filter: autobeam
BOEHME
CUT[ES IST IN DEINEN LIEDERN MEIN VOLK DIR PROPHEZEIT]
REG[Europa, Mitteleuropa, Deutschland]
KEY[B0029  08  C 4/4]
MEL[12  3_3_4_3_  522_0_
    23  4_4_6_54  3__0_
    1_  6_6_+1_76  655_0_
    +1_  5_355_42  1__0_
    1_  6_6_+1_76  655_0_
    +1_  5_355_42  1__0_ //] >>
FCT[politisch, national, Vaterlands - Lied]
</script>

<script>

// var vrvToolkit;

window.addEventListener("DOMContentLoaded", function() {
	// vrvToolkit = new verovio.toolkit();
	showMyEsac("source", "notation", "text");
});

function showMyEsac(sourceid, targetid, textid) {
	if (!vrvToolkit) {
		return;
	}
	var source = document.querySelector("#" + sourceid);
	var target = document.querySelector("#" + targetid);
	var text   = document.querySelector("#" + textid);
	var esac = source.textContent;

	if (!esac) {
		return;
	}
	if (!target) {
		return;
	}
	text.textContent = esac;
	var options = {
		inputFormat: "esac",
		adjustPageHeight: 1,
		pageHeight: 20000,
		pageWidth: 1300,
		spacingLinear: 0.24,
		spacingNonLinear: 0.55,
		spacingStaff: 1,
		scale: 50,
		font: "Leipzig"
	};
	var svg = vrvToolkit.renderData(esac, options);
	target.innerHTML = svg;
	target.style.marginTop = "-50px";
	target.style.marginLeft = "100px";
}

</script>

<br/>
<br/>
Fíjate en el uso de `!!!filter: autobeam` para unir las corcheas.


Consulta el [código fuente](https://raw.githubusercontent.com/humdrum-tools/vhv-documentation/gh-pages/myvhv/static-esac/index.md) de esta página para ver el javascript utilizado para crear la notación.  La principal diferencia con respecto a [Humdrum data display](/myvhv/static) es que el formato de entrada se establece como `"esac"`.


## Marcadores de frases analítica ##

En este ejemplo, la nota inicial de una frase se resalta en verde y la nota final en azul.  Esto se hace con el siguiente código CSS:


```CSS
.phraseStart { fill: green; }
.phraseStart [stroke] { stroke: green; }

.phraseStop { color: blue; }
.phraseStop [stroke] { stroke: blue; }

.phraseStart.phraseStop { color: orange; }
.phraseStart.phraseStop [stroke] { stroke: orange; }
```

Las frases se codifican implícitamente en los datos de EsAC mediante saltos de línea.  La primera nota de una línea es el inicio de la frase, y la última nota de una línea es el final de la frase.  Estas notas se etiquetan en el SVG con las clases `phraseStart` y `phraseStop` respectivamente. 


