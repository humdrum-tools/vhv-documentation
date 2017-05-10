---
title: Figured bass
author: Craig Stuart Sapp
keywords: humdrum figured bass
creation_date: 9 May 2017
last_updated: 9 May 2017
tags: [all, humdrum ]
verovio: true
vim: ts=3 ft=javascript
summary: A description of how to encode figured bass (basso continuo) in **fb spines.
sidebar: main_sidebar
permalink: /humdrum/figured_bass/index.html
---


Figured bass can be encoded in Humdrum `**fb` spines:

{% include verovio.html
	source="follia"
	humdrum-min-height="560px"
	scale="55"
	pageWidth="1000"
%}

<script type="application/json" id="follia">
!!!COM: Corelli, Arcangelo
!!!OTL: Follia in D minor, Op. 5, No. 12
**kern	**fb	**kern
*clefF4	*	*clefG2
*k[]	*	*k[]
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
.	6n	.
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
.	6n	.
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
.	3#	.
.	.	8cc#
=16	=16	=16
2.D	.	2.dd
=||	=||	=||
*-	*-	*-
</script>

Try changing/adding/deleting numbers in the second spine (column) to change 
the figured bass in the music on the right.

Accidental encodings match those of `**kern` pitches:

| Character | Meaning   |
| --------  | --------- | 
| #         | sharp     | 
| n         | natural   | 
| - (dash)  | flat      | 


Stacked figures are created by listing the numbers in order from top 
to bottom with a single space between the individual figures.
More complicated examples can be encoded once the verovio rendering
of figured bass has been completed.

Notice that figures do not need to be attached to notes on the staff that the 
figures are shown on (such as 3# in measure 15).

`**Bnum` can be used as an alias for `**fb`.

## Realization hints ##

Here is an example of adding realization hints in a basso continuo parts:

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
2F#N	4c#N	2D	76
.	4BN	.	.
*v	*v	*	*
4BN 4eN	4Gn	6
=	=	=
4A#N 4c#N 4f#N	4F#	#
2F#N 2BN 2dN	8EL	7 5 2
.	8D	_
.	8C#	_
.	8BBJ	_
=	=	=
2.A#N 2.c#N 2.f#N	4F#	#
.	4FF#	_
.	4GG#	_
=	=	=
4C#N 4F#N	4AA#	6
4EN 4G#N	4BB	6 4
4EN 4F#N 4A#N	4C#	6# 4 3
=	=	=
*v	*v	*
*-	*-
!!!RDF**kern: N = no stem, cue size
!!!URL: https://en.wikipedia.org/wiki/File:Figured_bass.png
</script>




