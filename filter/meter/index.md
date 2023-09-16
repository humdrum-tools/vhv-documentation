---
title: meter filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 15 Sep 2023
last_updated: 15 Sep 2023
ref: filters-meter
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/meter/index.html
---

The `meter` filter extracts metric information, such as beat positions
within a metrical cycle.

<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}


<h2> Basic example </h2>

Here is an example of beat labeling in different time signatures:

{% include verovio.html
	source="basicExample"
	scale="30"
	pageWidth="1450"
	humdrum-min-height="425px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample">
!!!filter: meter
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
4c
4d
4e
4f
=3
*M8/8
4c
4d
4e
4f
==
*-
</script>

<h2> Floating-point bests </h2>

<a name="option-f"></a>
Fractional beat positions are displayed as rational numbers by
default.  This can be changed to floating-point values by using the
`-f` option:

{% include verovio.html
	source="float"
	scale="30"
	pageWidth="1450"
	humdrum-min-height="425px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="float">
!!!filter: meter -f
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
4c
4d
4e
4f
=3
*M8/8
4c
4d
4e
4f
==
*-
</script>

<a name="option-c"></a>
Another styling option for fractional beat positions is `-c` to show a
comma instead of a decimal point:

{% include verovio.html
	source="comma"
	scale="30"
	pageWidth="1450"
	humdrum-min-height="425px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="comma">
!!!filter: meter -fc
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
4c
4d
4e
4f
=3
*M8/8
4c
4d
4e
4f
==
*-
</script>




<h2> Specifying the beat size </h2>

Time signatures such as 6/8, 9/8, and 12/8 are assumed to be compound
meters containing 2, 3 and or 4 beats respectively.  To switch to
a simple metric interpretation of such meters, us `*beat:8` to
define the beat as an eighth note rather than a dotted quarter note.
Using `*beat:4.` will redefine the beat as a dotted quarter note.
Note that the beat definition will be cleared whenever there is a
new time signature found for in the given spine.

{% include verovio.html
	source="compound-simple"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="compound-simple">
!!!filter: meter
**kern
*M6/8
=1
8cL
8d
8eJ
8fL
8g
8aJ
=2
*M6/8
*beat:8
8cL
8d
8eJ
8fL
8g
8aJ
=3
*beat:4.
8cL
8d
8eJ
8fL
8g
8aJ
=4
*beat:16
8cL
8d
8eJ
8fL
8g
8aJ
==
*-
</script>

<a name="option-r"></a>
<h2> Including rests in metric analysis </h2>

By default, rests are ignored when doing metric position analyses
of the music:

{% include verovio.html
	source="rest1"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="rest1">
!!!filter: meter
**kern
*M4/4
4c
2r
4d
=2
4c
4r
4e
4f
=
*-
</script>

Adding the `-r` option will add metric positions for rests, adding "r" after 
the position value to distinguish it from notes:

{% include verovio.html
	source="rest2"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="rest2">
!!!filter: meter -r
**kern
*M4/4
4c
2r
4d
=2
4c
4r
4e
4f
=
*-
</script>


<h2> Polymeter </h2>

Each staff (kern spine) can have an independent time signature, and beat
positions will be calculated based on the active time signature for each staff:

{% include verovio.html
	source="polymeter"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="polymeter">
!!!filter: meter
**kern	**kern	**kern
*M4/4	*M3/4	*M6/8
=1	=1	=1
4c	4c	8cL
.	.	8d
4d	4d	8eJ
.	.	8fL
4e	4e	8g
.	.	8aJ
=-	=2	=2
4f	4c	8cL
.	.	8d
=2	=-	=-
4c	4d	8eJ
.	.	8fL
4d	4e	8g
.	.	8aJ
=-	=3	=3
4e	4c	8cL
.	.	8d
4f	4d	8eJ
.	.	8fL
=3	=-	=-
4c	4e	8g
.	.	8aJ
=-	=4	=4
4d	4c	8cL
.	.	8d
4e	4d	8eJ
.	.	8fL
4f	4e	8g
.	.	8aJ
==	==	==
*-	*-	*-
</script>


<a name="option-z"></a>
<h2> Zero indexed beats </h2>

The `-z` option will start metric cycles with beat "0" rather than beat "1":

{% include verovio.html
	source="zero"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="zero">
!!!filter: meter | meter -z
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
2c
2d
=3
*M3/2
1.c
==
*-
</script>



<h2> Time-signature data extraction </h2>

<a name="option-t"></a>
The active time signature can be extracted for each note by using
the `-t` option:


{% include verovio.html
	source="tsig"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="tsig">
!!!filter: meter -t
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
2c
2d
=3
*M3/2
1.c
==
*-
</script>

The first line of data under the staff is the metric positions, and
the second line displays the active time signature for the note.


<a name="option-B"></a>
The time signature information can be displayed without showing the 
metric positions of notes by using the `-B` option:

{% include verovio.html
	source="tsig-only"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="tsig-only">
!!!filter: meter -tB
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
2c
2d
=3
*M3/2
1.c
==
*-
</script>

<h2> Time-signature components </h2>


<a name="option-n"></a>
<a name="option-d"></a>

The top and bottom parts of time-signatures can be extracted into
separate tandem spines.  The `-n` option can be used to extract the
"numerator" (top number of the time signature, and `-d` option can
extract the "denominator" (bottom number) of the time signature.

{% include verovio.html
	source="tsig-separate"
	scale="40"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="tsig-separate">
!!!filter: meter -Bnd
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
2c
2d
=3
*M3/2
1.c
==
*-
</script>

<h3> Joining time-signature and beats </h3>

The `-j` option can join the time signature and metric position
information into a single spine:

{% include verovio.html
	source="tsig-join"
	scale="40"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="tsig-join">
!!!filter: meter -j
**kern
*M4/4
=1
4c
4d
4e
4f
=2
*M2/2
2c
2d
=3
*M3/2
1.c
==
*-
</script>

<h2> Subspine behavior </h2>

When there are subspines for a given `**kern` spine, the analysis
data will interleave data of the subspines into a single analysis
spine:

{% include verovio.html
	source="subspine"
	scale="50"
	pageWidth="1300"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="subspine">
!!!filter: meter -fr
**kern
*M4/4
=1
*^
4cc	8gL
.	8fJ
2dd	4r
.	2g
4ff	.
=2	=2
2rdd	4re
.	4c
2dd	2d
*v	*v
=
*-
</script>





