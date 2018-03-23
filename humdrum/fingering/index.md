---
title: Fingering
author: Craig Stuart Sapp
keywords: humdrum fingering
creation_date: 23 Mar 2018
last_updated: 23 Mar 2018
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode fingerings in **fing spines.
sidebar: main_sidebar
permalink: /humdrum/fingering/index.html
---


Fingerings can be encoded in Humdrum `**fing` spines:

{% include verovio.html
	source="fingering"
	humdrum-min-height="460px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}

<script type="application/json" id="fingering">
!!!OTL: C major scale
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4c	1
4d	2
4e	3
4f	1
=2	=2
4g	2
4a	3
4b	4
4cc	5
=3	=3
4b	4
4a	3
4g	2
4f	1
=4	=4
4e	3
4d	2
2c	1
==	==
*-	*-
</script>


Fingerings can be placed in any order of spines after a `**kern` spine for the 
staff on which they should be displayed. Here is an example of including both
`**fing` and `**dynam` data for the same staff using 
J.S. Bach cello suite no. 1 in G major, BWV 1007, Menuet II.  The `**fing` and
`**dynam` spines can also be exchanged.

{% include verovio.html
	source="bwv1007"
	humdrum-min-height="460px"
	scale="55"
	tabsize="10"
	pageWidth="860"
%}

<script type="application/json" id="bwv1007">

!!!OTL: J.S. Bach
!!!OPR: Cello suite no. 1 in G major
!!!OTL: Menuet II
!!!SCA: BWV 1007
!!!ONB: mm 1-2
**kern	**fing	**dynam
*clefF4	*	*
*k[b-e-]	*	*
*M3/4	*	*
(8B-uL	2	p
8A	.	.
8B-)	.	.
(8D'	1	.
8E-'	2	.
8GG'J)	0	.
=2	=2	=2
4FF	1	.
(4A~	3	.
4D~)	0	.
=	=	=
*-	*-	*-

</script>

{% include warning.html
	content="Currently fingerings can only be shown above the staff, and chord fingerings will not be displayed properly."
%}


## Coloring fingerings with CSS ##

Fingerings are marked in the output SVG image from Verovio with the `fingering` class.
This allows fingerings to be styled on webpages like this:

{% include verovio.html
	source="dmajor"
	humdrum-min-height="460px"
	tabsize="10"
	scale="55"
	pageWidth="860"
%}

<script type="application/json" id="dmajor">
!!!OTL: D major scale
**kern	**fing
*clefG2	*
*M4/4	*
=1	=1
4d	1
4e	2
4f#	3
4g	1
=2	=2
4a	2
4b	3
4cc#	4
4dd	5
=3	=3
4cc#	4
4b	3
4a	2
4g	1
=4	=4
4f#	3
4e	2
2d	1
==	==
*-	*-
</script>


<style>

#dmajor-svg .fingering {
	fill: red;
}

</style>

Using the CSS definition:

```css
#dmajor-svg .fingering { fill: red; }
```



