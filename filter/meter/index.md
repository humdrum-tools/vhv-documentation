---
title: meter filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 15 Sep 2023
last_updated: 18 Sep 2023
ref: filters-meter
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/meter/index.html
---

The `meter` filter extracts metric information from a score, in
particular beat positions of notes within the active time signature.



<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}



<h2> Basic example </h2>

Without any additional options, the `meter` filter extracts beat
positions of notes according to the active time signature:

{% include verovio.html
	source="basicExample"
	scale="50"
	pageWidth="800"
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

In 4/4 time signatures, each quarter note is a beat.  For the
second measure in 2/2, the beat is at the half-note level, so the
second quarter note is halfway between beats 1 and 2.   This is
notated as `1+1/2` by default, but can be displayed as a floating-point
number (see next section below).  In 8/8, each quarter note is
equivalent to two eighth-note beats, so the four quarter notes are
interpreted as being on beats 1, 3, 5 and 7.



<h2> Floating-point beats </h2>

<a name="option-f"></a>
Off-beat positions are displayed as rational numbers by
default.  This can be changed to floating-point values by using the
`-f` option:

{% include verovio.html
	source="float"
	scale="50"
	pageWidth="800"
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

Now beat positions such as `1+1/2` and `2+1/2` are expressed as `1.5` and `2.5`.


<a name="option-D"></a>
For floating-point values, the `-D` option can control the number of digits after the decimal point.  Give
a value of 1 to 15 after the `-D` option, such as `-D 8` for up to eight digits after the decimal point:

{% include verovio.html
	source="float-digit"
	scale="50"
	pageWidth="800"
	humdrum-min-height="200px"
	humdrum-min-width="350px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="float-digit">
!!!filter: meter -f -D 5 | meter -f -D 3
**kern
*M6/8
=1
8cL
8d
8eJ
4.f
==
*-
</script>


<a name="option-c"></a>
Another styling option for fractional beat positions is `-c` which
displays a comma instead of a decimal point:

{% include verovio.html
	source="comma"
	scale="50"
	pageWidth="800"
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



<a name="tandem-beat"></a>
<h2> Explicit beat size encoding </h2>

Time signatures such as 6/8, 9/8, and 12/8 are assumed to be compound
meters containing 2, 3 and or 4 beats respectively.  To switch to
a simple metric interpretation of such meters, us `*beat:8` to
define the beat as an eighth note rather than a dotted quarter note.
Using `*beat:4.` will redefine the beat as a dotted quarter note.
Note that the beat definition will be cleared whenever there is a
new time signature found in the active staff/spine.

{% include verovio.html
	source="compound-simple"
	scale="50"
	pageWidth="800"
	spacingLinear="0.6"
	humdrum-min-height="525px"
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
!LO:TX:a:t=beat is now [eighth]
8c
8d
8e
8f
8g
8a
=3
*beat:4.
!LO:TX:a:t=beat reset to [quarter-dot]
8cL
8d
8eJ
8fL
8g
8aJ
=4
*beat:16
!LO:TX:a:t=beat set to [sixteenth]
8c
8d
8e
8f
8g
8a
=5
*M6/8
!LO:TX:a:t=beat automatically reset to [quarter-dot]
8cL
8d
8eJ
8fL
8g
8aJ

==
*-
</script>

Time signatures with a bottom number of 4 or smaller are always
treated automatically as a simple meter.  Here is an example of 
converting 6/4 into a compound meter using a dotted half note as
the beat:

{% include verovio.html
	source="compound-quarter"
	scale="50"
	pageWidth="800"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="compound-quarter">
!!!filter: meter
**kern
*M6/4
=1
!
4c
4d
4e
4f
4g
4a
!LO:LB:g=z
=2
*M6/4
*beat:2.
!LO:TX:a:t=compound meter with [half-dot] as the beat
4c
4d
4e
4f
4g
4a
!LO:LB:g=z
=3
*M6/4
!LO:TX:a:t=resets to simple meter by default
4c
4d
4e
4f
4g
4a
==
*-
!!!verovio: breaks encoded
</script>

<a name="option-w"></a>
<a name="option-h"></a>
<a name="option-q"></a>
<a name="option-e"></a>
<a name="option-s"></a>
<h2> Fixed-size metric units </h2>

By default metric positions are given in beats according to the
active time signature.  For example beats are quarter notes in 4/4,
but half notes in 2/2.  The following options can be used to 
extract metric positions in a fixed duration unit:

| Options | Meaning |
| ------- | ------- |
| `-w`    | whole note units |
| `-h`    | half note units |
| `-q`    | quarter note units |
| `-e`    | eighth note units |
| `-s`    | sixteenth note units |

{% include verovio.html
	source="fixed-duration"
	scale="50"
	pageWidth="800"
	humdrum-min-height="225px"
	humdrum-min-width="225px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="fixed-duration">
!!!filter: meter -s
!!!filter: meter -e
!!!filter: meter -q
!!!filter: meter -h
!!!filter: meter -w
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
==
*-
</script>


<a name="option-r"></a>
<h2> Including rests in metric analysis </h2>

By default, rests are ignored when doing beat analysis
of the music:

{% include verovio.html
	source="rest1"
	scale="50"
	pageWidth="800"
	humdrum-min-height="265px"
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

Adding the `-r` option will include beat positions for rests, adding
"r" after the position value to distinguish it from notes:

{% include verovio.html
	source="rest2"
	scale="50"
	pageWidth="800"
	humdrum-min-height="265px"
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
	scale="40"
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
	scale="50"
	pageWidth="800"
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
the `-t` option.  The first line of data under the staff is the
beat positions, and the second line displays the active time signature
for the note.


{% include verovio.html
	source="tsig"
	scale="50"
	pageWidth="800"
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



<a name="option-B"></a>

The time signature information can be displayed without showing the 
beat positions of notes by using the `-B` option:

{% include verovio.html
	source="tsig-only"
	scale="50"
	pageWidth="800"
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



<a name="option-n"></a>
<a name="option-d"></a>
<h2> Time-signature components </h2>

The top and bottom parts of time-signatures can be extracted into
separate tandem spines.  The `-n` option can be used to extract the
"numerator" (top number of the time signature, and `-d` option can
extract the "denominator" (bottom number) of the time signature.

{% include verovio.html
	source="tsig-separate"
	scale="50"
	pageWidth="800"
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

<a name="option-j"></a>
<h3> Joining time-signature and beats </h3>

The `-j` option can join the time signature and beat position
data into a single spine:

{% include verovio.html
	source="tsig-join"
	scale="50"
	pageWidth="800"
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

By default the complete time signature will be included, but using
`-n` or `-d` will add either the top or bottom numbers of the time 
signatures.   Here is an example using `-n`:

{% include verovio.html
	source="tsig-join-n"
	scale="50"
	pageWidth="800"
	humdrum-min-height="325px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="tsig-join-n">
!!!filter: meter -jn
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



<a name="option-L"></a>
<h2> Suppressing analysis spine labels </h2>

By default, output analysis spines are given labels such as "<i>beat:</i>"
for beat analysis spines:

{% include verovio.html
	source="beat-label"
	scale="50"
	pageWidth="800"
	humdrum-min-height="225px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="beat-label">
!!!filter: meter -m
**kern
*M4/4
=1
4c
4d
4e
4f
=
*-
</script>

These labels can be suppressed by adding the `-L` option:

{% include verovio.html
	source="beat-no-label"
	scale="50"
	pageWidth="800"
	humdrum-min-height="225px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="beat-no-label">
!!!filter: meter -mL
**kern
*M4/4
=1
4c
4d
4e
4f
=
*-
</script>

To label some spines and not others, multiple passes through the `meter`
filter can be made:


{% include verovio.html
	source="beat-no-label-some"
	scale="50"
	pageWidth="800"
	humdrum-min-height="225px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="beat-no-label-some">
!!!filter: meter -mB | meter -L
**kern
*M4/4
=1
4c
4d
4e
4f
=
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



<h2> Pickup measures </h2>

Pickup measures at the start of music are interpreted as being at the
end of a metric cycle rather than the start:

{% include verovio.html
	source="pickup"
	scale="50"
	pageWidth="800"
	humdrum-min-height="250px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="pickup">
!!!filter: meter
**kern
*M4/4
4c
4d
=1
4c
4d
4e
4f
=
*-
</script>



<h2> Split measures </h2>

Metric cycles split by a barline, such as for
repeat barlines, will be completed across the non-metric
barline:


{% include verovio.html
	source="split"
	scale="50"
	pageWidth="1200"
	humdrum-min-height="425px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="split">
!!!filter: meter -f
**kern
*M4/4
8d
=1
4c
4d
4e
4f
=1
4e
4d
=:|!|:
4e
4f
=2
4c
4d
4e
4f
=
*-
</script>



