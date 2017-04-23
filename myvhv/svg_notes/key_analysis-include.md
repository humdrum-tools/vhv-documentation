
## Key analysis directly from SVG images ## 

The following example generates a pitch-class histogram table
directly from the displayed SVG image.  As you mouse-over notes in
the image or rows in the table, all similar pitch-classes will be
highlighted in the notation.  The pitch histogram is also analyzed
to calculate an estimated musical key for the music, which is
displayed above the pitch-class table.  Columns in the table can be
sorted by clicking on the little arrows to the right of the column
headings.

Try editing the Humdrum data in the box below (or paste in new
data).  The notation should update as you change it, and the table
of pitch-class counts/durations further below should update as well.

{% include verovio.html
	source="myhumdrum"
	scale="40"
	border="0"
	spacingNonLinear="0.7"
	pageWidth="1850"
%}

<script type="text/humdrum" id="myhumdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8G\L
8E-\)
(8BBn\
8C\J)
4AA-/
=2
(8c\L
8A-\)
(8En\
8F\J)
4BBn/
=3
(8d\L
8A-\)
(8En\
8F\J)
(8GG\L
8G\J)
=4
(8F\L
8E-\)
(8BBn\
8C\J)
4CC/
=5
(8C\L
8E-\
8A-\)
(8G\
8d-X\
8c\J)
=6
(8D\L
8F\
8B-\)
(8A-\
8c\
8B-\J)
=7
(8A-\L
8G\)
(8D\
8E-\)
(8BB-\
8D\J)
=8
2.EE-/
=9:|!|:
(8B-\L
8G\)
(8D\
8E-\J)
4DD-X/
=10
(8B-\L
8G\)
(8En\
8F\J)
4GG/
=11
(8d-X\L
8B-\)
(8En\
8F\J)
8CC\L
8c\J
=12
(8B-\L
8A-\)
(8En\
8F\J)
4FF/
=13
(8EE-\L
8C\
8F\)
(8E-\
8B-\
8An\J)
=14
(8DD\L
8D\
8G\)
(8F\
8c\
8Bn\J)
=15
(8c\L
8A-\)
(8F#X\
8G\)
8BBn\
8C\J
=16
(8GG\L
8D\)
(8G\
8F#X\)
8c\
8Bn\J
=17
(8e-\L
8c\)
(8F#X\
8G\J)
8AAn\L
8e-\J
=18
(8d\L
8A-X\)
(8En\
8F\J)
8BBn\L
8G\J
=19
(8F\L
8E-\
8BBn\
8C\J)
(8GG\L
8Bn\J)
=20
(8CC/L
8GG/
8F/
8E-/J
4c\)
=:|!
*-
</script>

<style>
table.pitchmap {
	border-collapse: collapse;
	max-width: 500px;
}
.dataTables_info { display: none; }
table.pitchmap tr:hover td { background-color: red; }
table.pitchmap td { padding-left: 40px; }
table.pitchmap th { padding-left: 20px; }
table.pitchmap th { min-width: 150px;  max-width: 190px; }
table.pitchmap td { text-align: center; }
svg g.slur { opacity: 0.1; }
table.pitchmap th { min-width: 150px;  text-align:center; vertical-align: middle; max-width: 190px; }
table.pitchmap tr:hover {
	background-color: #ddddff;
}
</style>

<center>
<div id="estimate"></div>
<div id="pitchmap"></div>
</center>


<script>

var FILLCOLOR = "red";
var CURRENTPC = -1;

var Base40Counts  = [];
var Base40Durs = [];

var SvgTarget     = document.querySelector("#myhumdrum-svg");
var HumdrumTarget = document.querySelector("#myhumdrum-humdrum");
var Target        = document.querySelector("#pitchmap");

window.addEventListener("mousemove", function(event) {
	var matches;
	var target = event.target;
	while (target) {
		if ((target.nodeName == "TR") && (matches = target.id.match(/b40-(\d+)/))) {
			break;
		}
		if ((target.nodeName == "g") && (matches = target.className.baseVal.match(/b40-(\d+)/))) {
			break;
		}
		target = target.parentNode;
	}
	if (matches) {
		var pc = parseInt(matches[1]);
		if (pc == CURRENTPC) {
			return;
		}
		if (CURRENTPC >= 0) {
			hidePitchInSvg(CURRENTPC);
			hidePitchInTable(CURRENTPC);
		}
		CURRENTPC = pc;
		if (CURRENTPC >= 0) {
			showPitchInSvg(CURRENTPC);
			showPitchInTable(CURRENTPC);
		}
	} else {
		if (CURRENTPC >= 0) {
			hidePitchInSvg(CURRENTPC);
			hidePitchInTable(CURRENTPC);
		}
		CURRENTPC = -1;
	}
});

window.addEventListener("DOMContentLoaded", function() {
	extractPitchMap();
});

var observer = new MutationObserver(function(mutations) {
	mutations.forEach(function(mutation) {
		extractPitchMap();
   });
});
var config = { attributes: false, childList: true, characterData: false};
observer.observe(SvgTarget, config);


function extractPitchMap() {
	for (var i=0; i<40; i++) {
		Base40Counts[i] = [];
		Base40Durs[i] = 0;
	}
	var notes  = SvgTarget.querySelectorAll("svg g[class*='b40c-'");
	var matches;
	for (var i=0; i<notes.length; i++) {
		var content = notes[i].className.baseVal;
		if (matches = content.match(/b40c-([\d_]+)/)) {
			var b40 = matches[1];
			var b7 = base40ToBase7(b40);
			var dur = getDuration(content);
			Base40Durs[b40 % 40] += dur;
			Base40Counts[b40 % 40].push(notes[i]);
		}
	}
	var content = "<table class='pitchmap keytable'>";
	content += "<thead>";
	content += "<tr>";
	content += "<th>Pitch-class</th>";
	content += "<th>Note count</th>";
	content += "<th>PC Duration<br/> (in quarter notes)</th></tr>";
	content += "</thead>";
	content += "<tbody>";
	for (i=0; i<Base40Counts.length; i++) {
		if (Base40Durs[i] == 0) {
			continue;
		}
		content += "<tr id ='b40-" + i + "'>" ; content += "<td>" + base40ToName(i) + "</td>";
		content += "<td>" + Base40Counts[i].length + "</td>";
		content += "<td>" + round(Base40Durs[i], 3) + "</td>";
		content += "</tr>";
	}
	content += "</tbody>";
	content += "</table>";

//	$(Target.firstChild).dataTable().fnDestroy();
//	$(Target.firstChild).empty();
	Target.innerHTML = content;
   $(Target.firstChild).DataTable({
        paging: false,
        stateSave: true,
        searching: false,
		  destroy: true
    });

	findKey(Base40Durs);
}

function getDuration(content) {
	var ontime  = getRationalNumber(content, "qon-");
	var offtime = getRationalNumber(content, "qoff-");
	return offtime - ontime;
}

function getRationalNumber(content, prefix) {
	var matches;
	var output = 0;
	if (matches = content.match(new RegExp(prefix + "([\\d_]+)"))) {
		var ratnum = matches[1];
		if (matches = ratnum.match(/(\d+)_(\d+)/)) {
			output = parseInt(matches[1]) / parseInt(matches[2]);
		} else {
			output = parseInt(ratnum);
		}
	} else {
		output = 0;
	}

	return output;
}

function round(number, decdig) {
	var factor = Math.pow(10, decdig);
	return parseInt(number * factor + 0.5) / factor;
}

function showPitchInSvg(pc) {
	pc = pc % 40;
	var elements = Base40Counts[pc];
	for (var i=0; i<elements.length; i++) {
		elements[i].setAttribute("style", "fill: " +  FILLCOLOR);
	}
}

function hidePitchInSvg(pc) {
	pc = pc % 40;
	var elements = Base40Counts[pc];
	for (var i=0; i<elements.length; i++) {
		elements[i].removeAttribute("style");
	}
}

function showPitchInTable(pc) {
	pc = pc % 40;
	var element = document.querySelector("#b40c-" + pc);
	if (!element) {
		return;
	}
	if (element.nodeName == "TR") {
		var elements = element.querySelectorAll("td");
		element.style.backgroundColor = FILLCOLOR + " !important";
		for (var i=0; i<elements.length; i++) {
			elements[i].style["background-color"] = FILLCOLOR;
		}
	}
}

function hidePitchInTable(pc) {
	pc = pc % 40;
	var element = document.querySelector("#b40c-" + pc);
	if (!element) {
		return;
	}
	element.style["background-color"] = "";
	if (element.nodeName == "TR") {
		var elements = element.querySelectorAll("td");
		for (var i=0; i<elements.length; i++) {
			elements[i].style["background-color"] = "";
		}
	}
}

function base40ToBase7(b40) {
	var chroma = b40 % 40;
	var octaveoffset = parseInt(b40/40) * 7;
	if (b40 < 0) { return -1 }
	switch (chroma) {
		case 0: case 1: case 2: case 3: case 4: // Cbb to Cx
			return 0 + octaveoffset;
		case 6: case 7: case 8: case 9: case 10: // D-- to Dx
			return 1 + octaveoffset;
		case 12: case 13: case 14: case 15: case 16: // E-- to Ex
			return 2 + octaveoffset;
		case 17: case 18: case 19: case 20: case 21: // F-- to Fx
			return 3 + octaveoffset;
		case 23: case 24: case 25: case 26: case 27: // G-- to Gx
			return 4 + octaveoffset;
		case 29: case 30: case 31: case 32: case 33: // A-- to Ax
			return 5 + octaveoffset;
		case 35: case 36: case 37: case 38: case 39: // B-- to Bx
			return 6 + octaveoffset;
	}
	return -1;
}

function base40ToAccidentalName(b40) {
	var chroma = b40 % 40;
	switch (chroma) {
		case  0: case  6: case 12: case 17: case 23: case 29: case 35:
			return "&#x1d12b;";  // double flat
		case  1: case  7: case 13: case 18: case 24: case 30: case 36:
			return "&#x266d;";  // flat
		case  2: case  8: case 14: case 19: case 25: case 31: case 37:
			return  "";
			// return  "&#x266e;";  // natural
		case  3: case  9: case 15: case 20: case 26: case 32: case 38:
			return "&#x266f";  // sharp
		case  4: case 10: case 16: case 21: case 27: case 33: case 39:
			return "&#x1d12a;";  // double sharp
	}

	return -1000;
}

function base40ToDiatonicName(b40) {
	var base7 = base40ToBase7(b40);
	var chroma = base7 % 7;
	switch (chroma) {
		case 0: return "C";
		case 1: return "D";
		case 2: return "E";
		case 3: return "F";
		case 4: return "G";
		case 5: return "A";
		case 6: return "B";
	}
}

function base40ToName(base40) {
	var chroma = base40 % 40;
	var letter = base40ToDiatonicName(chroma);
	var accidental = base40ToAccidentalName(chroma);
	return letter + accidental;
}

function base12ToName(base12) {
	var chroma = base12 % 12;
	switch (chroma) {
		case  0: return "C";
		case  1: return "C#";
		case  2: return "D";
		case  3: return "Eb";
		case  4: return "E";
		case  5: return "F";
		case  6: return "F#";
		case  7: return "G";
		case  8: return "Ab";
		case  9: return "A";
		case 10: return "Bb";
		case 11: return "B";
	}
	return "X";
}


function findKey(hist) {
	var newhist = [0,0,0,0,0,0,0,0,0,0,0,0];
	newhist[0]  = hist[2]  + hist[6]  + hist[38]; //  0 = C + Dbb + B#
	newhist[1]  = hist[3]  + hist[7]  + hist[39]; //  1 = C# + Db + B##
	newhist[2]  = hist[4]  + hist[8]  + hist[12]; //  2 = C## + D + E--
	newhist[3]  = hist[9]  + hist[13] + hist[17]; //  3 = D# + E- + F--
	newhist[4]  = hist[10] + hist[14] + hist[18]; //  4 = D## + E + F-
	newhist[5]  = hist[15] + hist[19] + hist[23]; //  5 = E# + F + G--
	newhist[6]  = hist[16] + hist[20] + hist[24]; //  6 = E## + F# + G-
	newhist[7]  = hist[21] + hist[25] + hist[29]; //  7 = F## + G + A--
	newhist[8]  = hist[26] + hist[30]           ; //  8 = G# + A-
	newhist[9]  = hist[27] + hist[31] + hist[35]; //  9 = G## + A + B--
	newhist[10] = hist[32] + hist[36] + hist[0] ; // 10 = A# + B- + C--
	newhist[11] = hist[33] + hist[37] + hist[1] ; // 10 = A## + B + C-


	// from Bellman's CMMR 2005 paper
	var major = 
	{ "name": "major",
	"profile12": [
   16.80,	// C
    0.86,	// C#/Db
   12.95,	// D
    1.41,	// D#/Eb
   13.49,	// E
   11.93,	// F
    1.25,	// F#/Gb
   20.28,	// G
    1.80,	// G#/Ab
    8.04,	// A
    0.62,	// A#/Bb
   10.57 	// B
	]};

	var minor =
	{"name": "minor",
	"profile12": [
   18.16,	// C
    0.69,	// C#
   12.99,	// D
   13.34,	// D#
    1.07,	// E
   11.15,	// F
    1.38,	// F#
   21.07,	// G
    7.49,	// G#
    1.53,	// A
    0.92,	// A#
   10.21    // B
	]};

	var mixolydian = 
	{ "name": "mixolydian",
	"profile12": [
		2,		// C
		0,		// C#/Db
		1,		// D
		0,		// D#/Eb
		1,		// E
		1,		// F
		0,		// F#/Gb
		2,		// G
		0,		// G#/Ab
		1,		// A
		1,		// A#/Bb
		0		// B
	]};

	var lydian = 
	{ "name": "lydian",
	"profile12": [
		2,		// C
		0,		// C#/Db
		1,		// D
		0,		// D#/Eb
		1,		// E
		0,		// F
		1,		// F#/Gb
		2,		// G
		0,		// G#/Ab
		1,		// A
		0,		// A#/Bb
		1		// B
	]};

	var dorian = 
	{ "name": "dorian",
	"profile12": [
		2,		// C
		0,		// C#/Db
		1,		// D
		1,		// D#/Eb
		0,		// E
		1,		// F
		0,		// F#/Gb
		2,		// G
		0,		// G#/Ab
		1,		// A
		1,		// A#/Bb
		0		// B
	]};

	var phrygian = 
	{ "name": "phrygian",
	"profile12": [
		2,		// C
		1,		// C#/Db
		0,		// D
		1,		// D#/Eb
		0,		// E
		1,		// F
		0,		// F#/Gb
		2,		// G
		1,		// G#/Ab
		0,		// A
		1,		// A#/Bb
		0		// B
	]};

	var locrian = 
	{ "name": "locrian",
	"profile12": [
		2,		// C
		1,		// C#/Db
		0,		// D
		1,		// D#/Eb
		0,		// E
		1,		// F
		2,		// F#/Gb
		0,		// G
		1,		// G#/Ab
		0,		// A
		1,		// A#/Bb
		0		// B
	]};


	var data = {
		"hist12": newhist,
		"hist40": hist,
		// "profiles12": [major, dorian, phrygian, lydian, mixolydian, minor, locrian]
		"profiles12": [major, minor]
	}

	var i;
	for (var i=0; i<data.profiles12.length; i++) {
		generateKeyRatings(data.hist12, data.profiles12[i]);
	}


	maxmode = 0;
	maxtonic = 0;
	maxvalue = data.profiles12[0].correlation[data.profiles12[0].maxi];
	for (i=1; i<data.profiles12.length; i++) {
		var testvalue = data.profiles12[i].correlation[data.profiles12[i].maxi];
		if (testvalue > maxvalue) {
			maxmode = i;
			maxtonic = data.profiles12[i].maxi;
			maxvalue = testvalue;
		}
	}
	var estimate = document.querySelector("#estimate");
	var text = "estimated key: ";
	text += base12ToName((data.profiles12[maxmode].maxi) % 12)
	text += " " + data.profiles12[maxmode].name;
	estimate.innerHTML = text;
	// console.log(data);
}
	

function generateKeyRatings(hist, key) {
	var profile = key.profile12;
	key.correlation = [];
	for (var i=0; i<hist.length; i++) {
		key.correlation.push(pearsonCorrelation(hist, profile, i));
	}
	key.maxi = 0;
	for (i=1; i<key.correlation.length; i++) {
		if (key.correlation[i] > key.correlation[key.maxi]) {
			key.maxi = i;
		}
	}

	// console.log(key.name, key.maxi, key.correlation[key.maxi]);
}


function pearsonCorrelation(x, y, shift) {
	shift = shift || 0;
	var size = x.length;
	if (x.length != y.length) {
		size = Math.min(x.length, y.length);
		console.log("Using size", size, " elements of array for comparison");
	}
	if (size == 0) {
		return 0.0;
	}
	var sumx = 0.0;
	var sumy = 0.0;
	var sumco = 0.0;
	var meanx = x[(0 + shift) % size];
	var meany = y[0];
	var sweep;
	var deltax;
	var deltay;
	for (var i=2; i<=size; i++) {
      sweep = (i-1.0) / i;
      deltax = x[((i-1) + shift) % size] - meanx;
      deltay = y[i-1] - meany;
      sumx  += deltax * deltax * sweep;
      sumy  += deltay * deltay * sweep;
      sumco += deltax * deltay * sweep;
      meanx += deltax / i;
      meany += deltay / i;
   }
   var popsdx = Math.sqrt(sumx / size);
   var popsdy = Math.sqrt(sumy / size);
   var covxy  = sumco / size;
   return covxy / (popsdx * popsdy);
}

</script>

<br/>
<br/>
<br/>
<br/>

View the [Markdown source](https://github.com/humdrum-tools/vhv-documentation/blob/gh-pages/myvhv/svg_notes/key_analysis-include.md) 
for this page to view the JavaScript code for the example.


