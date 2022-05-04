---
title: synco filter
lang: en
ref: filters-synco
author: Craig Stuart Sapp
creation_date: 4 May 2022
last_updated: 4 May 2022
translator:
translation_date:
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/synco/index.html
---

The `synco` filter marks syncopated notes in a score.

<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}


<h2> Basic usage </h2>

A syncopation is defined as a note that is longer than the metric
level on which it starts.  For example a whole note in 2/1 that starts on
the second half-note of the measure is synocpated since it is starting on
a half-note level in the metric cycle, but it has a whole-note duration.

Currently the tool only works on music with a whole-note beat (i.e., Renaissance
music).


{% include verovio.html
	source="basicExample"
	scale="35"
	pageWidth="1600"
	tabsize="22"
%}
<script type="text/x-humdrum" id="basicExample">

!!!filter: synco
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
=20	=20	=20
0A	0r	2.e
.	.	4d
.	.	2e
.	.	2f
=21	=21	=21
0G	1r	0g
.	1B	.
=22	=22	=22
0F	2.c	0r
.	4B	.
.	2c	.
.	2d	.
=23	=23	=23
0E	0e	1r
.	.	1g
=24	=24	=24
1r	1.d	2.a
.	.	4g
1D	.	2a
.	4c	2b
.	4B	.
=25	=25	=25
1A	1A	1cc
1B	1G	[1dd
=26	=26	=26
1.G	1.g	2dd]
.	.	2cc
.	.	2b
4A	2f	2a
4B	.	.
=27	=27	=27
1c	2e	1g
.	2d	.
1A	1c	[1cc
=28	=28	=28
0G	1.d	2cc]
.	.	4b
.	.	4a
.	.	1b
.	2e	.
=29	=29	=29
2.D	[0f	2r
.	.	2.a
4C	.	.
4D	.	.
4E	.	4g
4F	.	4a
4G	.	4b
=30	=30	=30
2A	1f]	2cc
2B	.	2dd
2c	[1e	2r
4C	.	[2g
4BB	.	.
=31	=31	=31
4C	0e]	4g]
4D	.	4f
4E	.	4g
4F	.	4a
2G	.	2b
2A	.	2cc
=32	=32	=32
2B	[0d	2r
4BB	.	2.f
4AA	.	.
4BB	.	.
4C	.	4e
4D	.	4f
4E	.	4g
=33	=33	=33
2F	1d]	2a
2G	.	2b
2.A	[1c	2r
.	.	[2e
4G	.	.
=34	=34	=34
4A	0c]	4e]
4B	.	4d
4c	.	4e
4d	.	4f
2e	.	2g
2A	.	2a
=35	=35	=35
4B	[0B	2r
4A	.	.
4G	.	2.d
4F	.	.
4G	.	.
4A	.	4c
4B	.	4d
4c	.	4e
=36	=36	=36
2d	1B]	2f
2G	.	2g
2A	1A	1c
[2c	.	.
=37	=37	=37
2c]	1G	1d
2B	.	.
2c	2.c	2e
2A	.	[2c
.	4d	.
=38	=38	=38
2.c	2e	4c]
.	.	4d
.	2.c	4e
4d	.	4f
4e	.	2g
4f	4d	.
2g	4e	[2c
.	4f	.
=39	=39	=39
2r	1g	4c]
.	.	4d
2.c	.	4e
.	.	4f
.	2e	2g
4B	.	.
2A	2f	2a
=40	=40	=40
2G	1g	2r
2.g	.	2.c
.	2.c	.
4f	.	4d
4e	.	4e
4d	4d	4f
=41	=41	=41
4c	2e	2g
4B	.	.
2A	2f	2a
2G	1g	2b
2A	.	2cc
=42	=42	=42
2B	2G	2dd
2c	2.c	2.ee
2r	.	.
.	4B	4dd
[2c	4c	4ee
.	4d	4ff
=43	=43	=43
0c_	4e	2.ee
.	4d	.
.	4e	.
.	4f	4dd
.	1g	4ee
.	.	4ff
.	.	[2ee
=44	=44	=44
2c]	1a	4ee]
.	.	4dd
2F	.	4ee
.	.	4ff
2c	2g	4ee
.	.	4dd
2A	2a	4cc
.	.	4b
=45	=45	=45
2d	2f	2a
2G	2g	1g
2c	2e	.
2F	2f	[2cc
=46	=46	=46
1G	1d	2cc]
.	.	2b
1Cl	1cl	1ccl
==	==	==
*-	*-	*-
!!!RDF**kern: l=long note in original notation
!!!RDF**kern: i=editorial accidental
!!!verovio: evenNoteSpacing
</script>

{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=jrp/Jos/Jos2721-La_Bernardina.krn&filter=synco" %}

<a name="option-c"></a>
<h2> Highlight color</h2>

The `-c` option can be used to set the highlight color of syncopations
(any SVG color).


{% include verovio.html
	source="color"
	scale="40"
	pageWidth="1550"
	tabsize="10"
%}
<script type="text/x-humdrum" id="color">
!!!filter: synco -c crimson
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
=	=	=
*-	*-	*-
!!!RDF**kern: l=long note in original notation
!!!RDF**kern: i=editorial accidental
!!!verovio: evenNoteSpacing
</script>

{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=jrp/Jos/Jos2721-La_Bernardina.krn&filter=synco%20-c%20crimson" %}



<a name="option-i"></a>
<h2> Summary statistics </h2>

The `-i` option will show information about one or more input files, such as:


```
120     888     13.51%
180     1344    13.39%
117     881     13.28%
106     799     13.27%
148     1117    13.25%
190     1436    13.23%
309     2339    13.21%
203     1537    13.21%
80      610     13.11%
104     793     13.11%
```

The first number on a line is the number of syncopation notes in the file, the
second number is the number of notes in the file, and the third number is
the syncopation density (the fraction of notes in the score which are synopated).

When not using the `-i` option, the marked-up scores also include this information
in added reference records, such as:

```
!!!syncopated_notes: 33
!!!total_notes: 375
!!!syncopated_density: 8.8%
```

<a name="option-f"></a>
<h2> Add filename to summary statistics </h2>

The `-f` option adds the filename to each summary statistics line:

```
120	888	13.51%	Jos1002d-Missa_Missus_est_Gabriel_Angelus-Sanctus.krn
180	1344	13.39%	Jos0903b-Missa_Di_dadi-Gloria.krn
117	881	13.28%	Jos1003a-Missa_Quem_dicunt_homines-Kyrie.krn
106	799	13.27%	Jos1413-Si_dormiero.krn
148	1117	13.25%	Jos0401e-Missa_Ferialis-Agnus.krn
190	1436	13.23%	Jos0603d-Missa_Lhomme_arme_super_voces_musicales-Sanctus.krn
309	2339	13.21%	Jos2605-Gloria_laus_et_honor.krn
203	1537	13.21%	Jos0903e-Missa_Di_dadi-Agnus.krn
80	610	13.11%	Jos9919-Si_bibero.krn
104	793	13.11%	Jos0502e-Missa_Une_mousse_de_Biscaye-Agnus.krn
```


<a name="option-a"></a>
<h2> Average sycopation density </h2>

The `-a` option will average summary statistics for all input files.




