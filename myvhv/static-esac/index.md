---
title: Creating static in-browser images from EsAC data
lang: en
ref: myvhv-static-esac
author: Craig Stuart Sapp
vim: ts=3
creation_date: 10 Jun 2017
last_updated: 10 Jun 2017
sidebar: main_sidebar
tags: [all]
verovio: "true"
keywords: esac notation 
summary: "Simple use of the verovio javascript toolkit to display EsAC data as graphical notation on a stand-alone webpage with a tiny bit of javascript."
permalink: /myvhv/static-esac/index.html
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



The following music notation is generated from the EsAC data below.

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
Notice the use of `!!!filter: autobeam` to beam eighth notes together.


View the [source code](https://raw.githubusercontent.com/humdrum-tools/vhv-documentation/gh-pages/myvhv/static-esac/index.md)
for this page to view the javascript used to create the notation.  The main
difference from [Humdrum data display](/myvhv/static) is that the input format
is set to `"esac"`.


## Analytic phrase markers ##

In this example the starting note of a phrase is highlighted in green and the ending
note is highlighted in blue.  This is done with the following CSS code:


```CSS
.phraseStart { fill: green; }
.phraseStart [stroke] { stroke: green; }

.phraseStop { color: blue; }
.phraseStop [stroke] { stroke: blue; }

.phraseStart.phraseStop { color: orange; }
.phraseStart.phraseStop [stroke] { stroke: orange; }
```

Phrases are implicitly encoded in EsAC data by linebreaks.  The first note
on a line is the start of the phrase, and the last note on a line is the
end of the phrase.  These notes are labeled in the SVG with the classes
`phraseStart` and `phraseStop` respectively.



