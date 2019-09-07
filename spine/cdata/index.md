---
title: "**cdata"
lang: en
ref: data types
author: Craig Stuart Sapp
translator:
creation_date: 6 Sep 2019
translation_date:
last_updated: 7 Sep 2019
vim: ft=text
verovio: "true"
tags: [all, data_type]
sidebar: main_sidebar
keywords: data types
summary: "**cdata: for general text display as lyric text in music notation."
permalink: /spine/cdata/index.html
---

The `**cdata` spine type is used to display arbitrary textual data
in music notation as if it were chord labels.  The name is short
for "chord-like data".  Here is a basic example:


{% include verovio.html
	source="example1"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="example1">
**kern	**cdata
*M4/4	*
=1	=1
4c	a
4g	b
2c	c
.	d
=	=
4e	e
4r	f
2c	g
.	h
=	=
*-	*-
</script>


## Differences from **vdata ##

A [`**vdata`](/spine/vdata) spine is used to display text in a similar manner, but it can
only be displayed below the staff, and text cannot be associated with rests or a time positions
that do not have notes. 

{% include verovio.html
	source="both"
	humdrum-min-height="275"
	spacing-staff="0.8"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="both">
**kern	**vdata	**cdata
*M4/4	*	*
=1	=1	=1
4B	vdata:	cdata:
4c	a	1
2g	b	2
.	c	3
=2	=2	=2
4f	d	4
4r	e	5
4d	f	6
4c	g	7
==	==	==
*-	*-	*-
</script>


`**cdata` text cannot yet be shown below the staff, but it should be possible in the future.

## Refined positioning ##

`**cdata` text is positioned at a particular time.  Usually this time is inferred from the
contents of `**kern` spines.  However if you need to position in a way that cannot be
inferred, add a `**recip` spine to the data.  Each line of the `**recip` spine specifies
the duration of the line.

Blank `**kern` lines equally divide the duration of the previous
line into equal parts so in the following example, the `**cdata`
text `b`, `d`, `f`, and `h` are positioned half-way between the
half note (so at the quarter note positions):

{% include verovio.html
	source="half"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="half">
**kern	**cdata
*M4/4	*
=1	=1
2c	a
.	b
2d	c
.	d
=	=
2e	e
.	f
2c	g
.	h
=	=
*-	*-
</script>

An equivalent encoding using a `**recip` spine:

{% include verovio.html
	source="halfrecip"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="halfrecip">
**recip	**kern	**cdata
*	*M4/4	*
=1	=1	=1
4	2c	a
4	.	b
4	2d	c
4	.	d
=	=	=
4	2e	e
4	.	f
4	2c	g
4	.	h
=	=	=
*-	*-	*-
</script>

If you instead want to delay the text `b`, `d`, `f`, and `h` by an eight note, there needs
to be three blank lines after every half note to force the empty lines to be assigned
a duration of an eighth note:

{% include verovio.html
	source="eighth"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="eighth">
**kern	**cdata
*M4/4	*
=1	=1
2c	a
.	.
.	.
.	b
2d	c
.	.
.	.
.	d
=	=
2e	e
.	.
.	.
.	f
2c	g
.	.
.	.
.	h
=	=
*-	*-
</script>

This is somewhat fragile, since removing the null data lines (with `rid -d`) would cause the spacing
to revert to the original quarter-note level.  Here is the same result using a `**recip` spine:

{% include verovio.html
	source="eighthrecip"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="eighthrecip">
**recip	**kern	**cdata
*	*M4/4	*
=1	=1	=1
4.	2c	a
8	.	b
4.	2d	c
8	.	d
=	=	=
4.	2e	e
8	.	f
4.	2c	g
8	.	h
=	=	=
*-	*-	*-
</script>


## Multiple lines of data ##

Multiple lines of data can be given as separate `**cdata` spines.  The spines will be attached
to the staff created by the first `**kern` spine found to the left of the `**cdata` spines:

{% include verovio.html
	source="multiple"
	humdrum-min-width="400"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="multiple">
**kern	**cdata	**cdata	**kern	**cdata	**cdata
*M4/4	*	*	*M4/4	*	*
=1	=1	=1	=1	=1	=1
4.B	1st:	2nd:	4.dd	1st:	2nd:
8c	a	e	8ee	1	5
4g	b	f	4dd	2	6
4d	c	g	4b	3	7
=2	=2	=2	=2	=2	=2
1f	d	h	1a	4	8
==	==	==	==	==	==
*-	*-	*-	*-	*-	*-
</script>


## SVG labeling of data ##

The true data type of `**cdata` data can be given by adding a
hyphen after `**cdata` and then the name of the actual data type.
This will cause the text in the rendered SVG image of the notation
to be labeled with a class name based on the data type, and this
can then be manipulated by CSS, such as to highlight different
text data types in difference colors:


{% include verovio.html
	source="label"
	humdrum-min-width="400"
	humdrum-min-height="225"
	tabsize="15"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="label">
**kern	**cdata-letter	**cdata-number
*M4/4	*	*
=1	=1	=1
4B	1st:	2nd:
4c	a	1
4g	b	2
4d	c	3
=2	=2	=2
1f	d	4
==	==	==
*-	*-	*-
</script>

If you inspect the SVG image of the notation, you will see that the
text content includes class labels based on the data type given
after the dash in the `**cdata` spines, such as this SVG code for
displaying the number 3, where there is a `number` class added to
the first line. The other classname, `syl`, is a classname added
by verovio to indicate that the graphic element is a text syllable:

```xml
<g class="harm number" id="harm-L7F3">
   <text x="3353" y="323" font-size="0px">
      <tspan class="text" id="text-0000001671342372">
         <tspan font-size="405px" class="text" x="3353" y="323">3</tspan>
      </tspan>
   </text>
</g>
```


The text coloring and font changes are done with the following CSS code:


```css
svg .letter {
	fill: chartreuse;
  	text-shadow: 0px 0px 10px orange;
}

svg .number {
	fill: hotpink;
	font-family: Helvetica;
	font-weight: bold;
}
```


<style>
svg .letter {
	fill: chartreuse;
  	text-shadow: 0px 0px 10px orange;

}
svg .number {
	fill: hotpink;
	font-family: Helvetica;
	font-weight: bold;
}
</style>








