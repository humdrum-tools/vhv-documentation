---
title: "**vdata"
lang: en es
ref: data types
author: Craig Stuart Sapp
translator:
creation_date: 6 Sep 2019
translation_date:
last_updated: 6 Sep 2019
verovio: "true"
tags: [all, data_type]
sidebar: main_sidebar
keywords: data types
summary: "**vdata: for general text display as lyric text in music notation."
permalink: /spine/vdata/index.html
---

The `**vdata` data type is used to display arbitrary textual data
in music notation as if it were musical lyrics.  The name is short
for "verse-like data".  Here is a basic example:


{% include verovio.html
	source="example1"
	humdrum-min-height="375"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="example1">
**kern	**vdata
*M4/4	*
=1	=1
4c	a
4g	b
4d	c
4f	d
=2	=2
2c	e
.	f
2g	g
.	h
=3	=3
4c	i
4g	j
4r	k
4c;	l
==	==
*-	*-
</script>


Notice that the letters `f`, `h` and `k` are missing, since the
notation renderer, [verovio](https://www.verovio.org), cannot attach
lyrics to rests and cannot display lyrics where there is no note
(see the [`**cdata`](/spine/cdata) data type for doing that).

## Differences from **text ##

The [`**text`](/spine/text) data format is used to encode lyrics in Humdrum syntax.  This represention
maps spaces in the data contents to elision characters, while `**vdata` text preserves the space
in the rendered notation:

{% include verovio.html
	source="space"
	humdrum-min-height="225"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="space">
**kern	**text	**vdata
*M4/4	*	*
=1	=1	=1
4B	text:	vdata:
4c	a b c	a b c
4g	d e f	d e f
4d	g h i	g h i
=2	=2	=2
1f	j k l	j k l
==	==	==
*-	*-	*-
</script>


## Multiple lines of data ##

Multiple lines of data can be given as separate `**vdata` spines.  The spines will be attached
to the staff created by the first `**kern` spine found to the left of the `**vdata` spines:

{% include verovio.html
	source="multiple"
	humdrum-min-width="400"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="multiple">

**kern	**vdata	**vdata	**kern	**vdata	**vdata
*M4/4	*	*	*M4/4	*	*
=1	=1	=1	=1	=1	=1
4B	1st:	2nd:	4dd	1st:	2nd:
4c	a	e	4ee	1	5
4g	b	f	4dd	2	6
4d	c	g	4b	3	7
=2	=2	=2	=2	=2	=2
1f	d	h	1a	4	8
==	==	==	==	==	==
*-	*-	*-	*-	*-	*-
</script>


## SVG labeling of data ##

The true data type of `**vdata` data can be given by adding a
hyphen after `**vdata` and then the name of the actual data type.
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
**kern	**vdata-letter	**vdata-number
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
after the dash in the `**vdata` spines, such as this SVG code for
displaying the number 3, where there is a `number` class added to
the first line. The other classname, `syl`, is a classname added
by verovio to indicate that the graphic element is a text syllable:

```xml
<g class="syl number" id="syl-L7F3">
   <text x="3403" y="2337" font-size="0px">
      <tspan class="text" id="text-0000000746016912">
         <tspan font-size="405px" class="text">&nbsp;3</tspan>
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








