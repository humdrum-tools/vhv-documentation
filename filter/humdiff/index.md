---
title: humdiff filter
lang: en
ref: filters-humdiff
author: Craig Stuart Sapp
translator: 
creation_date: 15 Sep 2019
translation_date: 
last_updated: 15 Sep 2019
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/humdiff/index.html
---

The humdiff filter automatically identifies and marks differences
between two or more scores of the same music having the same duration.
The filter is useful for data validation when encoding scores using <a
target="_blank"
href="https://en.wikipedia.org/wiki/Two_pass_verification">double
data-entry method</a> as well as preparations of <a target="_blank"
href="https://chaucer.fas.harvard.edu/types-editions#criticaledition">critical
editions</a>.

Here are two example scores with some differences:

{% include verovio.html
	source="score1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-height="200px"
%}
<script type="text/x-humdrum" id="score1">
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
</script>


{% include verovio.html
	source="score2"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-height="200px"
%}
<script type="text/x-humdrum" id="score2">
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>


The humdiff filter identifies differences between the two scores
and will highlight notes in the first score that are different from
those in the second score:

{% include verovio.html
	source="humdiff1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiff1">
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>

Notice that the humdiff filter requires two (or more) data segments,
and the filtering command must start with four `!!!!`, indicating
that the filter applies to multiple data segments.


## Reference score ## 

By default, the humdiff filter will use the first data segment as
the reference score against which all of the other data segments
will be compared.  The reference score will be displayed with 
highlighted notes showing where other scores have different
pitches.

The `-r` option selects a different score in the Humdrum data stream
to use as the reference when it does not occur first.  Here is an
example of the same two scores being compared, but now the second
score in the data stream is used as the reference score:

{% include verovio.html
	source="humdiffr2"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffr2">
!!!!filter: humdiff -r 2
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>

Notice that the black notes in the resulting graphical score match
between the two versions of the music.  The highlighted notes are
different, and those of the reference edition are displayed.


An alternate method for selecting the reference score is to use the
[chooser filter](/filter/chooser).  This filter rearranges
the order of data segments within a stream of Humdrum data:

{% include verovio.html
	source="humdiffchooser"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchooser">
!!!!filter: chooser -s 2,1
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>


## Multiple score comparisons ##

The humdiff filter can compare multiple scores to a reference score,
provided that all scores have the same duration.  Any note in the
reference score that differs from a comparison score will be
highlighted.  Here is an example of three scores, with each having
one difference with the reference score.  The first score is a
C-major scale, the second one adds a sharp onto the F, and the third
adds a flat on the A.  This causes the F and A in the original score
to be highlighted:

{% include verovio.html
	source="humdiffmultiple"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-width="250px"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffmultiple">
!!!!filter: humdiff
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f#
=2
4g
4a
4b
4cc
==
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a-
4b
4cc
==
*-
</script>

Try changing the reference score in the above example, such as adding `-r 2` 
to the filter line in the above text.


## Highlighting color ##

The `-c` option can be used to set the highlighting color.  The color
can be any SVG/HTML color name or hex color.

{% include verovio.html
	source="humdiffcolor"
	scale="60"
	pageWidth="800"
	tabsize="16"
	humdrum-min-height="225px"
	humdrum-min-width="300px"
%}
<script type="text/x-humdrum" id="humdiffcolor">
!!!!filter: humdiff -c limegreen
**kern
*clefG2
*M4/4
=1
4c
4d
4e
4f
=
*-
**kern
*clefG2
*M4/4
=1
4c
4d
4g
4f
=
*-
</script>

Try setting the color to `hotpink` and `#ff8800`.


## Chopin mazurka example ##

Here is an example comparing the last two measures of Chopin's
mazurka in B minor, op 30/2, between two different first editions:
<ol>
<li> Breitkopf &amp; H&auml;rtel</li>
<li> Maurice Schlesinger</li>
</ol>

In the first comparison, the B&amp;H score is the reference, with red notes
indicating differences from the Schlesinger edition:


{% include verovio.html
	source="humdiffchopin"
	scale="60"
	pageWidth="900"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchopin">
!!!!filter: humdiff
!!!!SEGMENT: breitkopf
!!!OPS: 30
!!!OMN: 2
!!!PPR: Breitkopf & Härtel
!!!PPP: Leipzig
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e# 4c#	.	4ccc# 4cc#	.
4b 4e# 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[[
*clefF4	*	*	*
=64	=64	=64	=64
*ped	*	*	*
4FF#	2ff#)	4r	.
4f# 4c# 4F#	.	4cc# 4a	.
*Xped	*	*	*
4r	4ryy	4r	.
==	==	==	==
*-	*-	*-	*-
!!!!SEGMENT: schlesinger
!!!OPS: 30
!!!ONM: 2
!!!PPR: M. Schlesinger
!!!PPP: Paris
**kern	**kern	**dynam
*part1	*part1	*part1
*staff2	*staff1	*
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
*b:	*b:	*
*M3/4	*M3/4	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e 4c#	.	4ccc# 4cc#	.
4b 4e 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[
*	*v	*v	*
*clefF4	*	*
=64	=64	=64
4f# 4c# 4F#	4ff# 4a)	.
4F# 4FF#	4fff# 4ff#	fz
4r	4r	.
!!LO:TX:a:B:rj:t=FINE
==	==	==
*-	*-	*-
</script>

And in the following comparison, the Schlesinger edition is the
reference, with green notes being different from the B&amp;H edition:

{% include verovio.html
	source="humdiffchopin2"
	scale="60"
	pageWidth="900"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiffchopin2">
!!!!filter: chooser -s 2,1
!!!!filter: humdiff -c limegreen
!!!!SEGMENT: breitkopf
!!!OPS: 30
!!!OMN: 2
!!!PPR: Breitkopf & Härtel
!!!PPP: Leipzig
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e# 4c#	.	4ccc# 4cc#	.
4b 4e# 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[[
*clefF4	*	*	*
=64	=64	=64	=64
*ped	*	*	*
4FF#	2ff#)	4r	.
4f# 4c# 4F#	.	4cc# 4a	.
*Xped	*	*	*
4r	4ryy	4r	.
==	==	==	==
*-	*-	*-	*-
!!!!SEGMENT: schlesinger
!!!OPS: 30
!!!ONM: 2
!!!PPR: M. Schlesinger
!!!PPP: Paris
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[f#c#]	*k[f#c#]	*
=63	=63	=63
*	*^	*
8.bL 8.g#X 8.c#	2ryy	8.ee#XL 8.cc#	.
16bJk 16f# 16c#	.	16dddJk 16dd	.
4b 4e 4c#	.	4ccc# 4cc#	.
4b 4e 4c#	8gg#XL	4cc#	.
.	8aaJ	.	[
*	*v	*v	*
*clefF4	*	*
=64	=64	=64
4f# 4c# 4F#	4ff# 4a)	.
4F# 4FF#	4fff# 4ff#	fz
4r	4r	.
==	==	==
*-	*-	*-
</script>



