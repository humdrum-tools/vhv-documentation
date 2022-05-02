---
title: flipper filter
lang: en
ref: filters-flipper
author: Craig Stuart Sapp
translator: 
creation_date: 30 May 2021
translation_date: 
last_updated: 30 May 2021
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/flipper/index.html
---

The flipper tool is used to swap voices between spine splits.  The
tool is useful for correcting voicing errors when doing data entry.
See also the [spreadsheet interface](/interface/toolbar/spreadsheet)
for getting similar results, where columns can be swapped by copy
and pasted between spreadsheet cells manually.  The tool may will
be developed further to allow for dealing independently with strophes.

<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}


<a name="option-a"></a>
<h2> Flipping all spine splits </h2>

Using the `-a` option will cause all spine splits in the file to be swapped
such that the left subspine will be move to the right, and the right subspine
to the left.

Given this example score:

{% include verovio.html
	source="allinput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="250px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="allinput">
**kern
*M4/4
=1
*^
4g	4c
4a	4d
4b	4e
4cc	4f
*v	*v
=
*-
</script>

Here is the result of `flipper -a`, where the top voices is moved to the
bottom voice, and the bottom voice to the top voices (the strange orientation
of the stems is a visible manifestation of the flip):

{% include verovio.html
	source="alloutput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="250px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="alloutput">
!!!filter: flipper -a
**kern
*M4/4
=1
*^
4g	4c
4a	4d
4b	4e
4cc	4f
*v	*v
=
*-
</script>

Flipping twice will return the data to the original state:

{% include verovio.html
	source="alldouble"
	scale="60"
	pageWidth="600"
	humdrum-min-height="250px"
	humdrum-min-width="300px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="alldouble">
!!!filter: flipper -a | flipper -a
**kern
*M4/4
=1
*^
4g	4c
4a	4d
4b	4e
4cc	4f
*v	*v
=
*-
</script>

<h2> Flip control using *flip/*Xflip </h2>

Without options, the flipper tool will only flip regions of the score
that are found between `*flip` and `*Xflip` interpretations.  If there
are no `*flip` instructions in the file, flipper will not alter the file
(unless the `-a` option is given).

In the following example, only the second and third notes are 
flipped, and the notes outside of the `*flip`/`*Xflip` region(s):

{% include verovio.html
	source="flipXflip"
	scale="60"
	pageWidth="600"
	humdrum-min-height="300px"
	humdrum-min-width="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="flipXflip">
!!!filter: flipper
**kern
*M4/4
=1
*^
4g	4c
*flip	*
4a	4d
4b	4e
*Xflip	*
4cc	4f
*v	*v
=
*-
</script>

The `*flip` instruction can be placed in either subspine.



<a name="option-i"></a>
<h2> Flipping non-kern spines </h2>

By default Flipper is only applied to `**kern` spines.  To run on a different
exclusive interpretation type, use the `-i` option.

{% include verovio.html
	source="nonkerninput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="300px"
	humdrum-min-width="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="nonkerninput">
**kern		**text
*M4/4		*
=1		=1
*^		*^
4g	4c	A	1
4a	4d	B	2
4b	4e	C	3
4cc	4f	D	4
*	*	*v	*v
*v	*v	*
=	=
*-	*-
</script>

{% include verovio.html
	source="nonkernoutput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="300px"
	humdrum-min-width="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="nonkernoutput">
!!!filter: flipper -a -i text
**kern		**text
*M4/4		*
=1		=1
*^		*^
4g	4c	A	1
4a	4d	B	2
4b	4e	C	3
4cc	4f	D	4
*	*	*v	*v
*v	*v	*
=	=
*-	*-
</script>


<h2> Multiple subspines </h2>

All subspines will be flipped.  Here is an example with three subspines:

{% include verovio.html
	source="threeinput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="300px"
	humdrum-min-width="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="threeinput">
**kern	**text
*M4/4	*
=1	=1
*	*^
*	*^	*
4g	A	E	I
4a	B	F	J
4b	C	G	K
4cc	D	H	L
*	*v	*v	*v
=	=
*-	*-
</script>


For three subspines, the middle one will remain in place while the leftmost
and rightmost subspines will be swapped:

{% include verovio.html
	source="threeoutput"
	scale="60"
	pageWidth="600"
	humdrum-min-height="300px"
	humdrum-min-width="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="threeoutput">
!!!filter: flipper -a -i text
**kern	**text
*M4/4	*
=1	=1
*	*^
*	*^	*
4g	A	E	I
4a	B	F	J
4b	C	G	K
4cc	D	H	L
*	*v	*v	*v
=	=
*-	*-
</script>















