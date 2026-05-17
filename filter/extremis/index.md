---
title: extremis filter
lang: en
page_language: en
author: Alexander Morgan
creation_date: 17 May 2026
last_updated: 17 May 2026
ref: filters-extremis
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands analysis extremis continuo figured bass
summary: 
permalink: /filter/extremis/index.html
---

{% include filter-options.html file="options.aton" lang="EN" %}

The `extremis` filter creates one or two synthetic **kern spines containing the
lowest and/or highest sounding pitch at every moment in a score.  The tying and
beaming of the score is preserved as much as possible.  In some rare cases it is
possible for an attack to appear in the synthetic part that is not present in
the source score, however each note in the synthetic part does come from a note
in the source score.


## Default behavior ##

By default, `extremis` extracts the **lowest** sounding pitch at every moment
in the piece and generates a new synthetic `**kern` spine out of them.  The
synthetic spine uses a bass clef (`*clefF4`).  This behavior isthe default so no
flags are necessary, but if you wish you can explicitly specify it with `-l` 
(or `--low` or `--lowest`).

{% include verovio.html
	source="basic-lowest"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="basic-lowest">
!!!filter: extremis
**kern	**kern	**kern	**kern
*clefF4	*clefC3	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4	*M4/4
*k[]	*k[]	*k[]	*k[]
4C	4G	4e	4g
4D	4F	4d	4a
4E	4G	4c	4b
4C	4E	4g	4cc
=2	=2	=2	=2
4F	4A	4f	4cc
4G	4G	4e	4b
4A	4F	4d	4a
4G	4E	4e	4b
==	==	==	==
*-	*-	*-	*-
</script>


<a name="option-h"></a>
## Highest sounding pitches ##

Use the `-h` (or `--high` / `--highest`) option to extract the **highest**
sounding pitches instead.  The synthetic spine uses a treble clef (`*clefG2`).

{% include verovio.html
	source="highest-pitch"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="highest-pitch">
!!!filter: extremis -h
**kern	**kern	**kern	**kern
*clefF4	*clefC3	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4	*M4/4
*k[]	*k[]	*k[]	*k[]
4C	4G	4e	4g
4D	4F	4d	4a
4E	4G	4c	4b
4C	4E	4g	4cc
=2	=2	=2	=2
4F	4A	4f	4cc
4G	4G	4e	4b
4A	4F	4d	4a
4G	4E	4e	4b
==	==	==	==
*-	*-	*-	*-
</script>


<a name="option-b"></a>
## Both lowest and highest ##

Use the `-b` (or `--both`) option to extract **both** the lowest and highest
sounding pitches simultaneously.  Passing both `-l` and `-h` together produces
the same result.

{% include verovio.html
	source="both-extremes"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="both-extremes">
!!!filter: extremis -b
!!!COM: Bach, Johann Sebastian
!!!CDT: 1685/03/31-1750/07/28
!!!OPR@@DE: Die Kunst der Fuge
!!!OPR@EN: The Art of the Fugue
!!!OTL: Contrapunctus 1, a 4.
!!!SCA: BWV 1080
!!!voices: 4
!!!AGN: Simple fugue
**kern	**kern	**kern	**kern
*part4	*part3	*part2	*part1
*staff4	*staff3	*staff2	*staff1
*clefF4	*clefC4	*clefC3	*clefC1
*mclefF4	*mclefC3	*mclefG2	*mclefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*d:	*d:	*d:	*d:
*M2/2	*M2/2	*M2/2	*M2/2
*met(c|)	*met(c|)	*met(c|)	*met(c|)
*mmet(c|)	*mmet(c|)	*mmet(c|)	*mmet(c|)
*MM100	*MM100	*MM100	*MM100
=1	=1	=1	=1
1r	1r	2d	1r
.	.	2a	.
=2	=2	=2	=2
1r	1r	2f	1r
.	.	2d	.
=3	=3	=3	=3
1r	1r	2c#X	1r
.	.	4d	.
.	.	4e	.
=4	=4	=4	=4
1r	1r	[2f	1r
.	.	8fL]	.
.	.	8g	.
.	.	8f	.
.	.	8eJ	.
=5	=5	=5	=5
1r	1r	4d	2a
.	.	4e	.
.	.	4f	2dd
.	.	4g	.
=6	=6	=6	=6
1r	1r	4a	2cc
.	.	8AL	.
.	.	8BnJ	.
.	.	8cL	2a
.	.	8AJ	.
.	.	[4f	.
=7	=7	=7	=7
1r	1r	8fL]	2g#X
.	.	8BnJ	.
.	.	[4e	.
.	.	8eL]	4a
.	.	8f	.
.	.	8e	4bn
.	.	8dJ	.
=8	=8	=8	=8
1r	1r	4e	[2cc
.	.	4f#X	.
.	.	[2g	8ccL]
.	.	.	8dd
.	.	.	8cc
.	.	.	8b-XJ
!!LO:LB:g=original
=9	=9	=9	=9
2D	1r	4g]	8aL
.	.	.	8dJ
.	.	4f	2dd
2A	.	2e	.
.	.	.	4cc#X
=10	=10	=10	=10
2F	1r	4.d	8ddL
.	.	.	8aJ
.	.	.	[4ccn
.	.	8e	.
2D	.	4.f	8ccL]
.	.	.	8aJ
.	.	.	[4b-
.	.	8d	.
=11	=11	=11	=11
2C#X	1r	4.g	8b-L]
.	.	.	8eJ
.	.	.	[2.a
.	.	8g	.
4D	.	8fL	.
.	.	8e	.
4E	.	8d	.
.	.	8c#XJ	.
=12	=12	=12	=12
[2F	1r	4d	8a]
.	.	.	4cc
.	.	2g	.
.	.	.	8bn
8FL]	.	.	[2cc
8G	.	.	.
8F	.	4c	.
8EJ	.	.	.
=13	=13	=13	=13
2D	2A	4.f	8ccL]
.	.	.	8dJ
.	.	.	[4cc
.	.	8e	.
2r	2d	4.f	8cc]L
.	.	.	8aJ
.	.	.	[4bn
.	.	8G#X	.
=14	=14	=14	=14
4r	2c	2.e	4b]
8AAL	.	.	8aL
8BBnJ	.	.	8g#XJ
8CL	2A	.	2a
8AAJ	.	.	.
[4F	.	8dL	.
.	.	8cJ	.

==	==	==	==
*-	*-	*-	*-
</script>
