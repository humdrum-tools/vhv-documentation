---
title: composite filter
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 15 Sep 2019
last_updated: 22 Mar 2022
ref: filters-composite
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/composite/index.html
---

The `composite` filter extracts the composite rhythm of a score, which
is an intersection of note attacks from all staves in the score.
Music can be assigned to two groups to display separate polyrhythmic
streams of composite rhythms.

<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}


<h2> Simple composite rhythm </h2>

The basic usage of the `composite` filter without options collapses note rhythms 
from all parts into a single rhythm line.  Given the following score:

{% include verovio.html
	source="basicExample"
	scale="30"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample">
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>

{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn" %}


a composite rhythm line will be added underneath the original score:

{% include verovio.html
	source="basicExample2"
	scale="30"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample2">
!!!filter: composite
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn&filter=composite" %}


<a name="option-x"></a>
<h3> Display analysis only </h3>

The input score can be suppressed by adding the `-x` option, leaving
only the composite rhythm staff:


{% include verovio.html
	source="basicExample3"
	scale="40"
	marginTop="200"
	pageWidth="1200"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample3">
!!!filter: composite -x
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn&filter=composite%20-x" %}

<a name="option-l"></a>
<h3> Shrinking input or analysis parts </h3>

To emphasize the composite analysis, the `-l` option can be used
to shrink the input score.  To shrink the input score to 55%, use
`-l 55`:


{% include verovio.html
	source="basicExample4"
	scale="30"
	pageWidth="1300"
	pageMarginTop="150"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample4">
!!!filter: composite -l 55
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn&filter=composite%20-l55" %}

<a name="option-L"></a>
Try changinge the 55% value in the above text to change the size
of the original score.  Alternatively, the `-L` option can be used
to shrink the composite analysis:

{% include verovio.html
	source="basicExample5"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basicExample5">
!!!filter: composite -L 70
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn&filter=composite%20-L70" %}


<h3> System decoration adjustments </h3>

If the score has staff number interpretations, such as `*staff2`,
and a matching staff-decoration reference record, the analysis
data will be attached to the input score with a single line rather
than being included in the original system bracing or brackets.

{% include verovio.html
	source="systemDecoration"
	scale="30"
	pageWidth="1300"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="systemDecoration">
!!!filter: composite 
!!!system-decoration: [(s1,s2,s3,s4)]
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*staff4	*staff3	*staff2	*staff1
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>



<h3> System label </h3>

If parts in the score are labeled using an `*I"` interpretation, the composite
rhythm line will also be labeled.

{% include verovio.html
	source="systemLabel"
	scale="30"
	spacingLinear="0.2"
	spacingNonLinear="0.2"
	pageWidth="1550"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="systemLabel">
!!!filter: composite 
!!!system-decoration: [(s1,s2,s3,s4)]
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*staff4	*staff3	*staff2	*staff1
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*I'B	*I'T	*I'A	*I'S
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>


<a name="option-u"></a>
<h3> Analysis stem direction </h3>

By default the stem directions for the composite rhythm analysis will be down. To display
with stem-ups, add the `-u` option:

{% include verovio.html
	source="stemup"
	scale="30"
	spacingLinear="0.2"
	spacingNonLinear="0.2"
	pageWidth="1550"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="stemup">
!!!filter: composite -u
!!!system-decoration: [(s1,s2,s3,s4)]
**kern	**kern	**kern	**kern
*clefF4	*clefG2	*clefG2	*clefG2
*staff4	*staff3	*staff2	*staff1
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*I'B	*I'T	*I'A	*I'S
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*e:	*e:	*e:	*e:
*M4/4	*M4/4	*M4/4	*M4/4
*MM48	*MM48	*MM48	*MM48
=7	=7	=7	=7
8r	8eL	8gL	1r
*	*clefF4	*	*
8E	8F#J	8aJ	.
8EL	8GL	8bL	.
8EJ	8AJ	8ccJ	.
8D#L	4.B	16f#L	.
.	.	16g	.
8EJ	.	16f#	.
.	.	16eJ	.
[4F#	.	16d#L	.
.	.	16e	.
.	16AL	16f#	.
.	16BJ	16gJ	.
=8	=8	=8	=8
8F#]L	4.c	16aL	1r
.	.	16b	.
8EJ	.	16a	.
.	.	16gJ	.
[4A	.	[4f#	.
.	16BL	.	.
.	16c#J	.	.
8A]L	4.d	8f#]L	.
16G	.	16g	.
16F#J	.	16aJ	.
8BL	.	8gL	.
8AJ	16c#L	8f#J	.
.	16d#J	.	.
=9	=9	=9	=9
8GL	8eL	8eL	8r
8F#J	8AJ	8d#J	8b
8EL	16GL	16eL	8bL
.	16A	16f#	.
16D	16B	8gJ	8bJ
16EJ	16c#J	.	.
4.F#	8dL	4.f#	8a#L
.	16c#	.	8bJ
.	16BJ	.	.
.	[4A#	.	[4cc#
16EL	.	16gL	.
16F#J	.	16f#J	.
=10	=10	=10	=10
4.G	8A#]L	8eL	8cc#]L
.	16B	8dJ	8bJ
.	16A#J	.	.
.	8B	8r	[4ee
16F#L	8r	8dd	.
16G#J	.	.	.
4.A	8r	8cc#L	8ee]L
.	8e	8bJ	16dd
.	.	.	16cc#J
.	8c#L	16aL	8ff#L
.	.	16b	.
16G#L	8f#J	[8cc#J	8eeJ
16A#J	.	.	.
=	=	=	=
*-	*-	*-	*-
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=bach-wtc-fugues/wtc2f08.krn&filter=composite%20-u" %}

<h2> Polyrhythmic groupings </h2>

A score can be grouped into two separate composite rhythm streams
for use in polyrhythm analysis.  Each part or voice in a part can
be labeled with the interpretations `*grp:A` and `*grp:B`.  These
labels will then be used to split the score into two composite
rhythms.  Example scores with this markup can be found in the <a
target="_blank" href="https://verovio.humdrum.org/?file=poly">Polyrhythm
Project dataset</a> on VHV.

Here is an example score with group `A` and `B` labels:

{% include verovio.html
	source="group1"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="group1">
!!!COM: Janáček, Leoš [Leo Eugen]
!!!OTL: Pohádka (Fairy Tale) for Violoncello and Piano
!!!OMV: Movement 1
!!!example: 129
!!!work: Jan-30
!!!OMD-full: Con moto
!!!OMD: [Andante, un poco più mosso]
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129" %}

<a name="option-o"></a>
<h3> Extracting notes by group </h3>

The `-o` option (for <i>output</i>) can be used to extract notes from a particular group, here is an example
of extracting the group `A` notes:

{% include verovio.html
	source="groupA"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="groupA">
!!!filter: composite -o A
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-oA" %}

Notes in the other group will be converted into invisible rests.  And here is an extraction of the `B` group notes:

{% include verovio.html
	source="groupB"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="groupB">
!!!filter: composite -o B
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-oB" %}


<h3> Coloring groups in scores </h3>

To visualize the two groups in a score, use the `colorgroups` filter.  Group `A` will
be highlighted in red, and Group `B` will be shown in blue:


{% include verovio.html
	source="groupColor"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="groupColor">
!!!filter: colorgroups
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=colorgroups" %}

<a name="option-C"></a>
<h3> Coloring notes in the composite rhythm </h3>

The `-C` option can be used to also color notes in the full composite
rhythm according to which group the note is derived.  When the
composite rhythm note represents a note attack in both groups, then
it is colored green:

{% include verovio.html
	source="groupColorComposite"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="groupColorComposite">
!!!filter: composite -C | colorgroups
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-C|colorgroups" %}






<a name="option-g"></a>
<a name="option-F"></a>
<h3> Group composite rhythms </h3>

If a score has group labels, then the `-g` option can be used to
add composite rhythms for each groups:

{% include verovio.html
	source="group2"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="group2">
!!!filter: composite -g
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-g" %}

If the full composite rhythm is not desired, add the `-F` option to remove it:

{% include verovio.html
	source="group3"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="group3">
!!!filter: composite -gF
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-gF" %}


<a name="option-c"></a>
<h3> Coincidence analysis </h3>

The `-c` option can be added to generate a composite rhythm of the notes attacks that are shared
between group `A` and `B`:


{% include verovio.html
	source="coincidence1"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="coincidence1">
!!!filter: composite -cgF
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-cgF" %}


<a name="option-m"></a>
<h3> Marking coincidences </h3>

Use the `-m` option to mark notes in the score and composite analyses that are coincidence notes:

{% include verovio.html
	source="coincidence2"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="coincidence2">
!!!filter: composite -mgF
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-mgF" %}

<a name="option-M"></a>
To mark only the coincidence notes in the input score without displaying any analyses, use the `-M` option:

{% include verovio.html
	source="coincidence3"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="coincidence3">
!!!filter: composite -M
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-M" %}


<h2> Display and color all analyses </h2>

{% include verovio.html
	source="allanalyses"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1400"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="allanalyses">
!!!filter: composite -ugcmCl70 | colorgroups
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-ugcmCl70|colorgroups" %}

<h2> Numeric analyses </h2>

<a name="option-e"></a>
<h3> Event counts </h3>

The `-e` option can be added to show the event count for each 
composite rhythm staff at the start of the music:

{% include verovio.html
	source="eventCounts"
	scale="30"
	spacingLinear="0.1"
	spacingNonLinear="0.1"
	pageWidth="1650"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="eventCounts">
!!!filter: composite -ugce
**kern	**kern	**dynam	**kern	**dynam
*grp:A	*grp:B	*grp:B	*grp:A	*grp:A
*part2	*part2	*part2	*part1	*part1
*staff3	*staff2	*	*staff1	*
*ICklav	*ICklav	*	*ICstr	*
*Ipiano	*Ipiano	*	*Icello	*
*I"Piano	*	*	*I"Violoncello	*
*I'Pno.	*	*	*I'Vc.	*
*clefF4	*clefG2	*	*clefF4	*
*k[f#c#g#]	*k[f#c#g#]	*	*k[f#c#g#]	*
*A:	*A:	*	*A:	*
*M2/8	*M2/8	*	*M2/8	*
=124	=124	=124	=124	=124
*grp:A	*	*	*	*
*	*	*	*Xtuplet	*
!	!	!	!LO:TX:a:b:t=[[eighth]=84]	!
24EE\	8.Gn&lt;L	.	24r	.
*	*	*	*Xtuplet	*
!	!	!	!	!LO:DY:ed=brack
24ELL\	.	.	(24BB'LL	mf
24EJJ 24G	.	.	24BB'JJ 24E	.
8r	.	.	24BB'LL 24E	.
.	.	.	24BB'JJ 24E)	.
.	16B&lt;Jk)	.	.	.
!	!	!	!	!LO:DY:t=espress. %s
.	.	.	(24gn	f
=125	=125	=125	=125	=125
*^	*	*	*	*
*	*ped	*	*	*	*
*	*	*	*	*grp:B	*grp:B
!	!	!	!LO:DY:a	!	!
8ryy	24EE	(64ff#XLLLL	f	16aLL	.
.	.	64ee	.	.	.
!	!	!	!	!	!
!	!	!	!	!	!
.	.	64b	.	.	<
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
=126	=126	=126	=126	=126	=126
8C#X/	24C#X\	8r	.	(8.eL	.
.	24E'\LL	.	.	.	.
.	24E'JJ 24Gn	.	.	.	.
8BB/	24BB\	8r	.	.	.
.	24E'\LL	.	.	.	.
.	.	.	.	16gnJk)	.
.	24E'JJ 24G	.	.	.	.
=127	=127	=127	=127	=127	=127
*	*ped	*	*	*	*
8ryy	24EE	(64ff#XLLLL	.	(16aLL	.
.	.	64ee	.	.	.
.	.	64b	.	.	.
.	24E'LL	.	.	.	.
.	.	64gnJJJ	.	.	.
.	.	64cc#XLLL	.	16gn	.
.	.	64b	.	.	.
.	24E'JJ 24Gn	.	.	.	.
.	.	64g	.	.	.
.	.	64eJJJJ)	.	.	.
8BB/	24BB\	8r	.	16f#X	.
.	24E'\LL	.	.	.	.
.	.	.	.	16BJJ)	.
.	24E'JJ 24G	.	.	.	.
*v	*v	*	*	*	*
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: s1[({(s2,s3)})]
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=poly/129&filter=composite%20-ugce" %}

In addition, event counts are added at the bottom of the output
score in reference records for further numeric processing, such as
the following examples:

```tsv
!!!group-b-event-count: 24
!!!group-a-event-count: 24
!!!composite-event-count: 42
!!!coincidence-event-count: 6
```

These lines can be shown in VHV if the filter is compiled (causing the output
anlaysis score to replace the input score in the VHV text editor).

These values can then be processed automatically, such as extracting
the coincidence event count from the Humdrum score in a command-line
interface:

```bash
composite -ce file | grep "^\!\!\!coincidence-event-count:" | sed 's/.*: *//'
```

<a name="option-A"></a>
<h2> Numeric analysis features </h2>

Various analysis features can be extracted from a score along
with composite rhythms.  These are selected with the `-A` option.  Here is a list
of the characters than can be given in a string argument after the `-A` option flag:

| character | meaning |
| --------- | ------- |
| `n`       | notes onset count |


<h3> Note onset counts </h3>

To extract a count of note onsets for each composite rhythm event, add the 
letter `n` to the `-A` option string:

{% include verovio.html
	source="noteOnsetAnalysis"
	scale="31"
	spacingLinear="0.1"
	spacingNonLinear="0.3"
	pageWidth="1510"
	humdrum-min-height="200px"
	tabsize="10"
%}
<script type="text/x-humdrum" id="noteOnsetAnalysis">
!!!filter: composite -eCAn | colorgroups
!!!COM: Josquin des Prez
!!!OTL: La Bernardina
**kern	**kern	**kern
*staff3	*staff2	*staff1
*Ivox	*Ivox	*Ivox
*I"Contra	*I"Tenor	*I"Superius
*I'C	*I'T	*I'S
*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]
*C:	*C:	*C:
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-
4C	0r	0r
4D	.	.
4E	.	.
4F	.	.
2G	.	.
[2A	.	.
=2	=2	=2
4A]	0r	0r
4G	.	.
1c	.	.
2B	.	.
=3	=3	=3
1c	4C	0r
.	4D	.
.	4E	.
.	4F	.
2r	2G	.
[2F	[2A	.
=4	=4	=4
2F]	4A]	0r
.	4G	.
2E	1c	.
1D	.	.
.	2B	.
=5	=5	=5
2.C	[0c	4c
.	.	4d
.	.	4e
4D	.	4f
2E	.	2g
[2F	.	[2a
=6	=6	=6
4F]	1c]	4a]
4E	.	4g
2A	.	1cc
1G	1d	.
.	.	2b
=7	=7	=7
1C	1.e	1.cc
1r	.	.
.	2d	4b
.	.	4a
=8	=8	=8
1A	2e	2cc
.	2f	2dd
2G	2g	2b
[2A	2e	[2cc
=9	=9	=9
4A]	1.f	4cc]
4G	.	4b
4F	.	4a
4E	.	4g
2D	.	2a
[2A	2e	[2cc
=10	=10	=10
4A]	1.f	4cc]
4G	.	4b
4F	.	4a
4E	.	4g
2D	.	2a
[2A	2e	[2cc
=11	=11	=11
4A]	2f	4cc]
4G	.	4b
4F	1g	4a
4E	.	4g
1D	.	1a
.	2f#i	.
=12	=12	=12
2.G	0g	[0g
4A	.	.
2B	.	.
2c	.	.
=13	=13	=13
2.G	1r	0g]
4A	.	.
2B	1G	.
2E	.	.
=14	=14	=14
2.F	2.A	0r
4E	4G	.
1D	2A	.
.	2B	.
=15	=15	=15
0A	0c	1r
.	.	1c
=16	=16	=16
0G	0r	2.d
.	.	4c
.	.	2d
.	.	2e
=17	=17	=17
0F	1r	0f
.	1A	.
=18	=18	=18
0E	2.B	0r
.	4A	.
.	2B	.
.	2c	.
=19	=19	=19
0B	0d	1r
.	.	1d
=	=	=
*-	*-	*-
!!!RDF**kern: l=long note in original notation
!!!RDF**kern: i=editorial accidental
</script>
{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=jrp/Jos/Jos2721-La_Bernardina.krn&filter=composite%20-eCAn|colorgroups" %}


Here is an example of counting the note onsets for each event in
the full composite rhythm and then noting the metric position
of the event:


```bash
humcat h://jrp/Jos/Jos2721-La_Bernardina.krn | bin/composite -An \
	| beat -p | extractx -s 1,3 | ridx -H | sortcount -p | sort -k 3
```

```
2.24	.	0
1.35	6	1
3.59	8	1
4.04	1	1
4.93	2	1
4.93	3	1
6.73	4	1
7.17	7	1
8.52	5	1
1.79	8	2
11.21	1	2
2.69	2	2
2.69	6	2
4.04	4	2
5.83	7	2
7.17	3	2
7.17	5	2
0.45	8	3
1.79	3	3
3.59	5	3
4.04	1	3
4.04	7	3
```

11.21% of the cases are two note onsets occurring at the beginning
of a measure.  Three-note events occur at the half-note positions
(1, 3, 5, 7) with position 3 being about 1/2 as common as the other
positions.



