---
title: Figured bass
lang: en es
ref: humdrum-figured_bass
author: Craig Stuart Sapp
translator:
keywords: humdrum figured bass
creation_date: 9 May 2017
translation_date:
last_updated: 10 June 2019
tags: [all, humdrum, figured bass]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode figured bass (basso continuo) in **fb spines.
sidebar: main_sidebar
permalink: /humdrum/figured_bass/index.html
---


Figured bass can be encoded in Humdrum data using the `**fb` exclusive
interpretation.  Here is an example encoding:

{% include verovio.html
	source="follia"
	humdrum-min-height="900px"
	scale="55"
	pageWidth="1000"
%}

<script type="application/x-humdrum" id="follia">
!!!COM: Corelli, Arcangelo
!!!OTL: Follia in D minor, Op. 5, No. 12
!!!OMD: Adagio
**kern	**fb	**kern
*clefF4	*	*clefG2
*k[b-]	*	*k[b-]
*M3/4	*	*M3/4
=1-	=1-	=1-
2.D	.	4dd
.	.	4.dd
.	.	8ee
=2	=2	=2
2.AA	#	2cc#
.	.	4cc#
=3	=3	=3
2.D	5	4dd
.	.	(4.dd
.	6nr	.
.	.	16ccLL
.	.	16ddJJ)
=4	=4	=4
2.C	.	2ee
.	.	4ee
=5	=5	=5
2.F	.	4ff
.	.	4.ff
.	.	8gg
=6	=6	=6
2C	.	2ee
4C#	6	4ee
=7	=7	=7
4D	.	(8ddL
.	.	8cc#J)
2BB-	7	4.dd
.	6	8ee
=8	=8	=8
2.AA	#	2cc#
.	.	4cc#
=9	=9	=9
2.D	.	4dd
.	.	4.dd
.	.	8ee
=10	=10	=10
2.AA	#	2cc#
.	.	4cc#
=11	=11	=11
2.D	5	4dd
.	.	(4.dd
.	6nr	.
.	.	16ccLL
.	.	16ddJJ)
=12	=12	=12
2.C	.	2ee
.	.	4ee
=13	=13	=13
2.F	.	4ff
.	.	4.ff
.	.	8gg
=14	=14	=14
4.C	.	4.ee
8C#	6	8ee
4D	.	4ff
=15	=15	=15
4GG	7 5	4dd
2AA	5 4	4.dd
.	X 3#r	.
.	.	8cc#
=16	=16	=16
2.D	.	2.dd
=||	=||	=||
*-	*-	*-
</script>

Try changing/adding/deleting numbers in the second spine (column)
to change the figured bass in the music on the right.

Notice that figures do not need to be attached to notes on the staff
where figures are displayed (such as `3#` in measure 15).

## Stacked figures ##

Stacked figures, specifying more than one interval above the bass
note, are created by listing the numbers in order from top to bottom
and separating each figure with a single space.  Here are some examples
of displaying more than one figure simultaneously:

{% include verovio.html
	source="stacked"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="stacked">
**kern	**fb
*M4/4	*
=1	=1
4g	7
4g	7 5
4g	7 5 3
4g	6 4
==	==
*-	*-
</script>

### Stack placeholders ###

Use `X` or `x` to add an empty placeholder in a figured-bass stack.
Upper-case `X` characters mean that any line extensions should
terminate at this position, while lowercase `x` means that any
extension line from a previous figure should pass through this position.

{% include verovio.html
	source="placeholder"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="placeholder">
**kern	**fb
*M4/4	*
=1	=1
2c	7_ 4:
2c	x 3
=2	=2
1c	7 4:3
=	=
*-	*-
</script>

A colon (:) indicates that a hyphen should follow the figure, if
it is at the end of a figure.  If it is in the middle of a figure,
then the colon should also be rendered as a hyphen, and it separates
two figures from each other.


{% include warning.html
	content="Verovio does not yet render line extensions for figures, so an underscore will currently be substituted for the extension line.  Similarly, hyphens centered between sequential figures are not representable in MEI yet (and hence not renderable in verovio, so a place-holder hyphen is displayed after the first figure)."
%}

### Implicit intervals ###

A figure such as "6" is shorthand for "6 3".  For analytic purposes,
explicitly encoding the "3" interval as well as the "6" may be
useful, yet display only the "6".  To do this, add a "K" to a figure
to suppress its visual display.  This is similar to "X" and "x",
but in the case of those two signifiers, no interval is implied.
Unlike `X`/`x`, the `K` signifier will not preserve a vertical
position for the invisible figure; however, you may include both
`K` and `X` signifiers on the same figure to both hide the figure
and preserve the stack position.

{% include verovio.html
	source="hidden"
	humdrum-min-height="280px"
	scale="55"
	pageWidth="950"
	spacingNonLinear="0.35"
	spacingLinear="0.8"
%}

<script type="application/json" id="hidden">
**kern	**fb
*M4/4	*
=1	=1
4g	6
4g	6 3
2g	6 3K
=2	=2
4f	5K 3K
4f	6K 4 2
4f	X 4 2
4f	6KX 4 2
=	=
1f	7 5K 3K
=	=
*-	*-
</script>





## Staff placement ##

By default, figures will be placed below the staff.  To move them
above, add the interpretation `*above` before the first figure that
should be placed above the staff.  Use `*below` to revert to the
default position below the staff.

{% include verovio.html
	source="above"
	scale="55"
	humdrum-min-height="320px"
	pageWidth="500"
%}

<script type="application/json" id="above">
**kern	**fb
*M4/4	*
*	*above
=1	=1
4e	6
4e	5
4e	4 2
4e	6 4 2
=2	=2
4e	6
4e	5
*	*below
4e	4 2
4e	6 4 2
==	==
*-	*-
</script>



## Accidentals ##

Accidental encodings match those of `**kern` pitches:

| Character       | Meaning            |
| --------------- | ------------------ | 
| #               | sharp              | 
| n               | natural            | 
| &ndash; (dash)  | flat               | 
| ##              | double-sharp       | 
| &ndash;&ndash;  | double-flat        |

### Encoding written versus sounding accidentals ###

In `**fb` encodings, accidentals have a fixed meaning that is similar
to modern music notation: A sharp means one half-step above a natural
diatonic pitch, and a flat means one half-step below a natural
diatonic pitch.  In seventeenth-century music, the meaning of an
accidental can be relative, such that a sharp sign for a note/figure
that is otherwise flat means to raise the pitch by a half-step to
the natural diatonic position.  And likewise, flat signs may lower
a sharped pitch to its natural state.

In such cases, add an "n" after the sharp or flat sign.  When a
natural sign is present at the same time as a sharp or flat, the
natural sign is the sounding accidental for the figure, and the
sharp or flat is the written sign.  The following example demonstrates
this behavior: in the first measure there is a written sharp sign
for an interval which would otherwise be a B-flat due to the key
signature.  This should be interpreted to raise the B-flat pitch
to B-natural.  For the second measure, the modern convent of writing
a natural to cancel the flat is used.

{% include verovio.html
	source="relative"
	tabsize="10"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="relative">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
1g	#n
=2||	=2||
1g	n
==	==
*-	*-
</script>

In both measures of the above example, a G-major chord should be
played. For the first measure, the sharp functions as a relative
accidental, and in the second measure, the natural sign is an
absolute accidental.


### Switching between relative and absolute visual accidentals ###

Add the tandem interpretation `*absolute` to the figure-bass spine
to display accidentals in a modern style rather than the relative
accidental style of the seventeenth century (if relative accidentals
are encoded in the data). The allows easy switching between original
notation and modern conventions.  To cancel forced display of
absolute accidentals, insert the `*Xabsolute` tandem interpretation
before the figures to which it applies.

Here is a similar example, but an absolute accidental replaces the
original relative accidental in the first measure:

{% include verovio.html
	source="absolute"
	tabsize="10"
	scale="55"
	pageWidth="580"
	spacingNonLinear="0.40"
	spacingLinear="0.45" 
	minLastJustification="0.50"
	humdrum-min-height="300px"
%}

<script type="application/json" id="absolute">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
*	*absolute
!!LO:TX:a:i:t=absolute
1g	#n
=2	=2
1g	n
=3||	=3||
*	*Xabsolute
!!LO:TX:a:i:t=relative
1g	#n
=4	=4
1g	n
==	==
*-	*-
</script>

### Encoding chromatic interval  ###

Using absolute accidentals for figured bass can cause problems when
transposing music with figured bass.  For example "&#x266E;7" in C
major with a bass-note on C will produce a major seventh on B-natural,
while the same figure in G major with a bass-note on G will produced
an F-natural, which is a minor seventh.

The main problem is that in order to calculate the exact pitch of
the figure, both the alteration of the figure and the key signature
of the music is needed.  So for encoding the exact chromatic interval,
the letters `m`, `M`, `P`, `d` and `A` may be prefixed to the figure
number:

| Character       | Meaning                    |
| --------------- | -------------------------- | 
| m               | minor interval             | 
| M               | major interval             | 
| P               | perfect interval           | 
| d               | diminished interval        | 
| dd              | doubly diminished interval | 
| A               | augmented interval         | 

The `d` and `A` characters may be repeated, with each additional
letter lowering or rasising the pitch by a half-step.

These chromatic interval signifiers will not directly affect the
visual display of accidentals on notes, but they are necessary for
adjusting absolute accidentals when transposing music.  An "fb"
tool will be written to automatically insert chromatic alteration
letters.  This tool should also be able to adjust figured-bass
accidentals after transposition.

### Accidentals after figure numbers ###

Add an `r` to a figure to reverse the order of accidentals and
numbers.  The position of the sharp and the number is not otherwise
important in the `**fb` encoding as demonstrated below:

{% include verovio.html
	source="reverse"
	tabsize="10"
	scale="55"
	pageWidth="800"
%}

<script type="application/json" id="reverse">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
4f	n6 n6r
4f	n6 6nr
4f	n6 6rn
4f	n6 r6n
==	==
*-	*-
</script>

Alternatively, give the tandem interpretation, `*reverse`, somewhere
before the first figure to reverse the position of accidentals
to avoid encoding reverse styling with `r` on every single
token.  Use `*Xreverse` to turn off the reversing feature.

{% include verovio.html
	source="reverse2"
	tabsize="10"
	humdrum-min-height="350px"
	scale="55"
	pageWidth="400"
%}

<script type="application/json" id="reverse2">
**kern	**fb
*M4/4	*M4/4
*k[b-e-]	*k[b-e-]
=1	=1
!!LO:TX:a:t=normal
2f	n6
2f	n6
=2	=2
*	*reverse
!!LO:TX:a:t=reverse
2f	n6
2f	n6
=3	=3
*	*Xreverse
!!LO:TX:a:t=individual
2f	n6r
2f	n6r
==	==
*-	*-
</script>


## Slashed figures ##

In some figured-bass notational conventions, slashes are used 
instead of accidentals to raise or lower the chromatic alteration
of a figure.  Slashes moving down from left to right typically mean
that the chromatic alteration should be raised by a half-step,
while slashes moving up from left to right mean that the
figure's pitch should be lowered by a half-step.  Another variation
is to use a `+` sign to indicate raising the pitch by a half-step.
The `+` sign may also be stylized to be attached to the numeral
of the figure.

Any figure can be slashed in `**fb` data, but not all of them are renerable
in verovio notation.  Here is a sampler of the ones that are available in
graphic notation:

{% include verovio.html
	source="slashes"
	tabsize="10"
	humdrum-min-height="400px"
	scale="55"
	pageWidth="800"
	spacingLinear="0.9"
	spacingNonLinear="0.2"
%}

<script type="application/json" id="slashes">
**kern	**fb
=-	=-
1f	#2 #2|
=-	=-
1f	#4 #4|
=-	=-
1f	#6 #6|
=-	=-
1f	-5 -5/
=-	=-
1f	#5 #5\
=-	=-
1f	#5 #5|
=-	=-
1f	#7 #7\
=-	=-
1f	-7 -7/
=-	=-
1f	#7 #7|
==	==
*-	*-
</script>

Here are the types of slashes that can be encoded:

| Character       | Visual rendering | Typical meaning                       |
| --------------- | ---------------- | ------------------------------------- | 
| \               | slash going down | raise by half-step from key signature | 
| /               | slash going up   | lower by half-step from key signature | 
| \|              | vertical slash   | raise by half-step from key signature | 

### Displaying figures without slashes ###

Accidentals should also be encoded in figures to explicitly indicate
the chromatic alteration of the figure.  Currently the MusicXML
improter (see below) does not add such accidentals.  The parallel
accidental encoding is required since the meaning of slashes across
different styles is not always consistent, so slashes in the encodings
should be viewed as entirely visual elements, not analytic elements.

Figure bass can be automatically converted from slash notation to accidental notation
for altered figures.  Add the `*Xslash` tandem interpretation to display accidentals
instead of slashes.

{% include verovio.html
	source="noslashes"
	tabsize="10"
	humdrum-min-height="400px"
	scale="55"
	pageWidth="800"
	spacingLinear="0.9"
	spacingNonLinear="0.2"
%}

<script type="application/json" id="noslashes">
**kern	**fb
=-	=-
1f	#2 #2|
=-	=-
1f	#4 #4|
=-	=-
1f	#6 #6|
=-	=-
1f	-5 -5/
=-	=-
1f	#5 #5\
=-	=-
1f	#5 #5|
=-	=-
1f	#7 #7\
=-	=-
1f	-7 -7/
=-	=-
1f	#7 #7|
==	==
*-	*-
</script>


## Editorial signifiers ##

There are three types of editorial signifiers for `**fb` data: `i` indicates editorial 
intervention, displaying figures/accidentals in square brackets; `j` indicates editorial
intervention, displaying figures/accidentals in parentheses; and `k` indicates editorial
intervention, not visualizing figures/accidentals.  Here is a sampler of each type
of editorial markup:

{% include verovio.html
	source="editorial"
	tabsize="10"
	humdrum-max-height="325px"
	lyricTopMinMargin="4.0"
	spacingLinear="0.30"
	scale="55"
	pageWidth="500"
	minLastJustification="0.25"
%}

<script type="application/json" id="editorial">
**kern	**fb	**text
*clefG2	*	*
*	*above	*
=1	=1	=1
4c	#6i	i
4c	#6ir	ir
4c	#6I	I
=2	=2	=2
4c	#6j	j
4c	#6jr	jr
4c	#6J	J
=3	=3	=3
4c	#6k	k
4ryy	.	.
4c	#6K	K
=	=	=
*-	*-	*-
</script>


Note that lowercase codes apply only to the accidental, while
uppercase codes apply to the entire figure.



## Negative numbers ##

If you want to display a negative figured bass number, you can use the `~` signifier
in front of the number to prefix it with a minus sign.

E.g. to encode the exact distances between two voices with an *intervallsatz*:


{% include verovio.html
	source="negative"
	tabsize="10"
	humdrum-max-height="325px"
	lyricTopMinMargin="4.0"
	spacingLinear="0.30"
	scale="55"
	pageWidth="500"
	minLastJustification="0.25"
%}

<script type="application/json" id="negative">
**kern	**fb	**kern	**fb
*clefG2	*	*clefG2	*
*k[b-]	*	*k[b-]	*
*M4/4	*	*M4/4	*
*met(c|)	*	*met(c|)	*
16r	.	[4a	.
16g	.	.	2
16f	.	.	3
16e	.	.	4
=	=	=	=
8f	.	16a]	3
.	.	16f	1
8aa	.	16d	~12
.	.	16f	~10
8e	.	16g	3
.	.	16e	1
8gg	.	16c#	#~12
.	.	16e	~10
16d	.	8f	3
16gg	.	.	~9
16ff	.	8d	~10
16ee	.	.	~9
16dd	.	[4d	~8
16cc	.	.	~7
16b-	.	.	~6
16a	.	.	~5
=	=	=	=
*-	*-	*-	*-
!!!filter: autobeam
</script>



## Adding figured-bass spines in VHV ##

To add a figured-bass spine to music in the VHV editor, do these
three steps:

1. Type this filter line (anywhere in the file):
```
!!!filter: extract -s 1,0,2-$
```
The filter assumes you have multiple parts or spines, and that you
want to insert the figured bass spine as the second column from the left.
The "0" in the extraction spine inserts a blank spine between spines
1 and 2.  The spine extraction string will be different if you want to
place the `**fb` spine elsewhere.
2. Compile the filter by typing <span class="keypress">alt-c</span>.  For 
some keyboard/OS configurations, you may need to click on the graphic
music on the right first (if <span class="keypress">alt-c</span>
inserts a character in the text, for example).  After compiling the 
filter, the filter label should change to `Xfilter` and the blank
spine should become visible in the text editor.

3. Change the exclusive interpretation of the new spine from
`**blank` to `**fb`.  You can also remove the used filter line.

Here is a video demonstrating the process:


{% include image.html
	file="adding-fb.gif"
	alt="Demonstration of adding a figured-bass spine."
	max-width="100%"
	caption="Demonstration of adding a figured-bass spine using the extract filter."
%}


## Importing figured bass from MusicXML ##

VHV can import figured bass from MusicXML data.  Note that some
music editors, such as MuseScore, can create/export figured bass,
but others, such as Finale, cannot.  To convert a MusicXML file
with figured bass, drag-and-drop the file onto the VHV webpage.

{% include image.html
	file="musicxml-fb.gif"
	alt="MusicXML import with figured bass"
	max-width="100%"
	caption="MusicXML file containing figured bass, exported from MuseScore, then imported by drag/drop file into VHVV."
%}

<a target="_blank" href="musicxml-fb.xml">Here</a> is the 
MusicXML test file used in the above video.

## Realization hints ##

Here is an example of adding realization hints in a basso continuo part:

{% include verovio.html
	source="beschrankt"
	humdrum-min-height="560px"
	scale="55"
	pageWidth="1000"
%}

<script type="application/json" id="beschrankt">
!!!COM: Bach, Johann Sebastian
!!!OTL: Beschränkt, ihr Weisen
!!!SCT: Riemenschneider no. 47/69
**kern	**fb
*clefF4	*
*k[f#c#g#]	*
*M3/4	*
*^	*
4G#N 4BN	4E	.
4AN 4eN	4C#	6
4AN 4c#N	4F#	.
=	=	=
*^	*	*
2F#N	4c#N	2D	7:
.	4BN	.	6
*v	*v	*	*
4BN 4eN	4Gn	6
=	=	=
4A#N 4c#N 4f#N	4F#	#
2F#N 2BN 2dN	8EL	7_ 5_ 2_
.	8D	.
.	8C#	.
.	8BBJ	.
=	=	=
2.A#N 2.c#N 2.f#N	4F#	#_
.	4FF#	.
.	4GG#	.
=	=	=
4C#N 4F#N	4AA#	6
4EN 4G#N	4BB	6 4
4EN 4F#N 4A#N	4C#	6#/ 4 3
=	=	=
*v	*v	*
*-	*-
!!!RDF**kern: N = no stem, cue size, color=#bbbbbb
!!!URL: https://en.wikipedia.org/wiki/File:Figured_bass.png
</script>


<script>

//////////////////////////////
//
// DOMContentLoaded event listener --
//

document.addEventListener("DOMContentLoaded", function () {
	var containerSelector = "#beschrankt-svg"
	var svgSelector = containerSelector + " svg";
	var color = "#aaa";
	var interval = setInterval(function () {
		var svgTargetElement = document.querySelector(containerSelector);
		if (!svgTargetElement) {
			return;
		}
		clearInterval(interval);
		var observer = new MutationObserver(function (mutations) {
			mutations.forEach(function (mutation) {
				color514(svgSelector, color);
   		});
		});
		var config = { attributes: false, childList: true, characterData: false };
		observer.observe(svgTargetElement, config);
		// Have to color manually the first time since SVG is already in place:
		color514(svgSelector, color);
	}, 100);
});


//////////////////////////////
//
// color514 -- color notes with size 514 in gray.
//

function color514(selector, color) {
	var item = document.querySelector(selector);
	var notes = item.querySelectorAll("g.note");
	for (var i=0; i<notes.length; i++) {
		var use = notes[i].querySelector("use");
		if (!use) {
			continue;
		}
		var height = use.getAttribute("height");
		if (height !== "514px") {
			continue;
		}

		var par = notes[i].parentNode;
		if (par.classList && par.classList[0] !== "chord") {
			notes[i].style.fill = color;
			notes[i].style.stroke = color;
		} else {
			par.style.fill = color;
			par.style.stroke = color;
		}
	}

}

</script>


<style>
svg g.ledgerLines.cue [stroke]
	 { fill: #999;     stroke: #999; }
</style>


Here is Javascript code for implementing the above example:


```javascript
document.addEventListener("DOMContentLoaded", function () {
   var containerSelector = "#beschrankt-svg"
   var svgSelector = containerSelector + " svg";
   var color = "#aaa";
   var interval = setInterval(function () {
      var svgTargetElement = document.querySelector(containerSelector);
      if (!svgTargetElement) {
         return;
      }
      clearInterval(interval);
      var observer = new MutationObserver(function (mutations) {
         mutations.forEach(function (mutation) {
            color514(svgSelector, color);
         });
      });
      var config = { attributes: false, childList: true, characterData: false };
      observer.observe(svgTargetElement, config);
      // Have to color manually the first time since SVG is already in place:
      color514(svgSelector, color);
   }, 100);
});

function color514(selector, color) {
   var item = document.querySelector(selector);
   var notes = item.querySelectorAll("g.note");
   for (var i=0; i<notes.length; i++) {
      var use = notes[i].querySelector("use");
      if (!use) {
         continue;
      }
      var height = use.getAttribute("height");
      if (height !== "514px") {
         continue;
      }
      var par = notes[i].parentNode;
      if (par.classList && par.classList[0] !== "chord") {
         notes[i].style.fill = color;
         notes[i].style.stroke = color;
      } else {
         par.style.fill = color;
         par.style.stroke = color;
      }
   }
}

```

And the CSS styling for the example to also color ledger lines of notes:

```css
svg g.ledgerLines.cue [stroke]
	 { fill: #999;     stroke: #999; }
```


