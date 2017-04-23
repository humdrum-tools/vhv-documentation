<!-- 
	vim: ts=3 ft=javascript 
-->

## Coloring stems, beams, and ties ##

The following example demonstrates a more complicated setup for coloring
all aspects of the notation.  Pitch classes control the coloring of 
noteheads, stems, tied and beams, with the beams being given a 
color gradient according to the pitch classes of the first and last
note in the beam.


{% include verovio.html
	source="coloredbeams"
	pageWidth="950"
	scale="60"
%}

<script type="application/humdrum" id="coloredbeams">
**kern
*M4/4
*clefG2
*k[f#]
8dL
8gJ
=1
2e
8r
8d
8gL
8aJ
=2
2.g
8bL
8ddJ
=3
[2ee
8ee]L
8ddJ
8bL
8aJ
=4
2.b
8gL
8gJ
=5
[2b
8b]L
8gJ
8aL
8gJ
=6
[2d
8d]L
8dJ
8eL
8dJ
=7
8gL
8dJ
8gL
8bJ
4.a
8g
=8
2.g
==
*-
</script>

<style>
#coloredbeams-svg .pname-c, #coloredbeams-svg .pname-c [stroke]
	 { fill: green;     stroke: green; }
#coloredbeams-svg .pname-d, #coloredbeams-svg .pname-d [stroke]
	 { fill: blue;      stroke: blue; }
#coloredbeams-svg .pname-e, #coloredbeams-svg .pname-e [stroke]
	 { fill: firebrick; stroke: firebrick; }
#coloredbeams-svg .pname-f, #coloredbeams-svg .pname-f [stroke]
	 { fill: gold;      stroke: gold; }
#coloredbeams-svg .pname-g, #coloredbeams-svg .pname-g [stroke]
	 { fill: lightblue; stroke: lightblue; }
#coloredbeams-svg .pname-a, #coloredbeams-svg .pname-a [stroke]
	 { fill: purple;    stroke: purple}
#coloredbeams-svg .pname-b, #coloredbeams-svg .pname-b [stroke]
	 { fill: orange;    stroke: orange; }

#coloredbeams-svg .clef,
#coloredbeams-svg .rest,
#coloredbeams-svg .keySig,
#coloredbeams-svg .meterSig,      /* time signatures */
#coloredbeams-svg .barLineAttr,   /* barlines */
#coloredbeams-svg .staff > path,  /* staff lines */
#coloredbeams-svg .system > use   /* measure numbers */
{
	opacity: 0.15;
}
</style>



<script>
//
// Set up a mutation watch to update the SVG coloring whenever a new
// SVG is generated.
//

var observer2 = new MutationObserver(function(mutations) {
	mutations.forEach(function(mutation) {
		colorall("#coloredbeams-svg > svg");
   });
});
var config2 = { attributes: false, childList: true, characterData: false};
var SvgTarget2 = document.querySelector("#coloredbeams-svg");
observer2.observe(SvgTarget2, config2);


//////////////////////////////
//
// colorall -- Color beams and ties in the notation Color beams and 
//     ties in the notation.
//

function colorall(selector) {
	insertFilters(selector);
	var notes = document.querySelectorAll("#coloredbeams-svg .note");
	var beams = document.querySelectorAll("#coloredbeams-svg .beam");
	var ties  = document.querySelectorAll("#coloredbeams-svg .tie");
	for (var i=0; i<ties.length; i++) {
		colorTie(ties[i], notes);
	}
	for (i=0; i<beams.length; i++) {
		colorBeam(beams[i], notes);
	}
}



//////////////////////////////
//
// colorTie -- Color a tie according to the pitch class of the first note.
//

function colorTie(tie, notes) {
	var matches;
	if (!(matches = tie.id.match(/tie-([^-]+)/))) {
		return;
	}
	var note;
	var noteid = "note-" + matches[1];
	for (var i=0; i< notes.length; i++) {
		if (notes[i].id == noteid) {
			note = notes[i];
		}
	}
	if (!note) {
		return;
	}
	var pname = "";
	for (i=0; i<note.classList.length; i++) {
		if (note.classList[i].match(/^pname-/)) {
			pname = note.classList[i];
		}
	}
	if (!pname) {
		return;
	}
	tie.setAttribute("class", tie.getAttribute("class") + " " + pname);
}



//////////////////////////////
//
// colorBeam -- Color a beam according to the first and last note's pitch classes.
//

function colorBeam(beam, notes) {
	var matches;
	var id1;
	var id2;
	if (!(matches = beam.id.match(/beam-([^-]+)-([^-]+)/))) {
		return;
	}
	var note1;
	var note2;
	var noteid1 = "note-" + matches[1];
	var noteid2 = "note-" + matches[2];
	for (var i=0; i< notes.length; i++) {
		if (notes[i].id == noteid1) {
			note1 = notes[i];
		}
		if (notes[i].id == noteid2) {
			note2 = notes[i];
		}
	}
	if (!note1) { return; }
	if (!note2) { return; }

	var pname1 = "";
	var pname2 = "";
	for (i=0; i<note1.classList.length; i++) {
		if (note1.classList[i].match(/^pname-/)) {
			pname1 = note1.classList[i];
		}
	}
	for (i=0; i<note2.classList.length; i++) {
		if (note2.classList[i].match(/^pname-/)) {
			pname2 = note2.classList[i];
		}
	}
	if (!pname1) { return; }
	if (!pname2) { return; }

	if (pname1 === pname2) {
		beam.setAttribute("class", beam.getAttribute("class") + " " + pname1);
	}

	var filter = "filter_" + (pname1 + pname2).replace(/pname-/g, "");
	beam.setAttribute("fill", "url(#" + filter + ")");
}



//////////////////////////////
//
// Insert all possible two pitch-class gradients into the SVG.
//

function insertFilters(selector) {
	var svg = document.querySelector(selector);
	if (!svg) {
		return;
	}
	var colors = {};
	colors["c"] = "green";
	colors["d"] = "blue";
	colors["e"] = "firebrick";
	colors["f"] = "gold";
	colors["g"] = "lightblue";
	colors["a"] = "purple";
	colors["b"] = "orange";

	content = "";
	for (var key1 in colors) {
		if (!colors.hasOwnProperty(key1)) {
			continue;
		}
		for (var key2 in colors) {
			if (!colors.hasOwnProperty(key1)) {
				continue;
			}
			if (key1 === key2) {
				continue;
			}
			content += "<linearGradient id='filter_" + key1 + key2 + "'>\n";
			content += "<stop offset='5%'  stop-color='" + colors[key1] + "'></stop>\n";
			content += "<stop offset='95%' stop-color='" + colors[key2] + "'></stop>\n";
			content += "</linearGradient>\n";
		}
	}

   var svgns = "http://www.w3.org/2000/svg";
	var defs = document.createElementNS(svgns, "defs");
	defs.innerHTML = content;
	svg.insertBefore(defs, svg.firstChild);
}


</script>


View the 
[Markdown source](https://github.com/humdrum-tools/vhv-documentation/blob/gh-pages/myvhv/svg_notes/colored_beams-include.md)
for this page to view the JavaScript code for the example.



