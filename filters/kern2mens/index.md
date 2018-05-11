---
title: kern2mens filter
author: Craig Stuart Sapp
creation_date: 10 May 2018
last_updated: 10 May 2018
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filters/kern2mens/index.html
---

The _kern2mens_ filter can be used to convert `**kern` data (modern western
music notation) into `**mens` (white mensural notation).

Here is an example use of kern2mens to convert modern notation into
white mensural notation:

{% include verovio.html
	source="example1"
	scale="60"
	pageWidth="1100"
	humdrum-min-width="250"
%}

<script type="application/x-humdrum" id="example1">
!!!filter: kern2mens
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>


Try removing the first data line starting with `!!!filter:` to see the
original modern notation.

With [VHV](http://verovio.humdrum.org), you can view the converted `**mens`
data by typing `alt-c` to compile the filter.  For the above example, this will
produce data that looks like this:

{% include verovio.html
	source="example1b"
	scale="60"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example1b">
**mens
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
siF
SiA
.
siF
=3-
siB-
siG
=4-
siG
sp:A
.
MiG
siF
=6-
SiE
=7-
siF
SiA
.
siF
=9-
siB-
siG
=10-
siG
sp:A
.
miG
miF
siG
=12-
SiF
=17-
siF
Sic
.
sie-
=19-
Sid
=20-
sic
siA
=21-
siB-
siG
=22-
SiF
=23-
siF
Sic
.
sie-
=27-
Sid
=28-
sic
siA
=29-
siB-
siG
=30-
SiF
=||
*-
</script>


The converted data may not be completely syntactically correct and
may require further edition &mdash; such as removing perfection
dots in circle mensurations (this will be improved in the future).  The
kern2mens filter is still in development mode, so expect bugs.
For example, the first E4 (top line) should be flat, and the second
one should have an editorial flat above it.

A future development will allow specifying an "original clef" in the modern notation
which will be used in the `**mens` data.  Such a clef would be like a regular
`**kern` clef, but with an `o` prefixed to "clef", such as `*oclefC3` for an alto
clef.  Currently the `-c` option can be used to change the clef between the
`**kern` and `**mens` notation display.  Here is the same music as above, but
setting the `**mens` clef to C3 from the filter line:



{% include verovio.html
	source="example2"
	scale="60"
	humdrum-min-width="250"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example2">
!!!filter: kern2mens -c C3
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>

Barlines are still needed in the converted data so that verovio can break
the music onto mulple lines.  Notice that tied notes are merged into single
notes in the conversion.  Any barlines that split a note will be removed,
but the rest will be left for layout purposes.  You can remove the barlines
by adding the `-M` option, but this is currently only useful for short
single-line examples. 

If you want to remove bar numbers from the measures,
add the `-N` option to the filter. If you want to keep the barlines, then
add the `-I` option. Here is an example of using the `-N` and `-I` options
at the same time:

{% include verovio.html
	source="example2b"
	scale="60"
	humdrum-min-width="250"
	pageWidth="1100"
%}

<script type="application/x-humdrum" id="example2b">
!!!filter: kern2mens -c C3 -NI
**kern
*I"Tenor
*clefC4
*k[b-]
*M2/1
*met(C|)
=1-
1F
[1A
=2
1A]
1F
=3
1B-
1G
=4
1G
[1A
=5
2A]
2G
1F
=6
0E
=7
1F
[1A
=8
1A]
1F
=9
1B-
1G
=10
1G
[1A
=11
2A]
4G
4F
1G
=12
0F
=17
1F
[1c
=18
1c]
1e-
=19
0d
=20
1c
1A
=21
1B-
1G
=22
0F
=23
1F
[1c
=26
1c]
1e-i
=27
0d
=28
1c
1A
=29
1B-
1G
=30
0F
==
*-
</script>

Notice that some of the barlines have been remove to avoid tied notes in the converted
`**mens` data.



Text underlay (i.e., lyrics) can be given as a `**text` spine to the right
of the `**kern` and resulting `**mens` spine:

{% include verovio.html
	source="example-text"
	scale="40"
	humdrum-min-width="250"
	pageWidth="1200"
%}

<script type="application/x-humdrum" id="example-text">
!!!filter: kern2mens -cC1 -N
**kern	**text
*staff1	*staff1
*Ivox	*
*I"Superius	*
*I'S	*
*clefG2	*
*k[]	*
*M2/1	*
*met(C|)	*
=8	=8
0b	Dul-
=9	=9
0cc	-ces
=10	=10
1.cc	ex-
4b	.
4a	.
=11	=11
1a	-u-
[1cc	-vi-
=12	=12
2cc]	.
4b	.
4cc	.
2b	.
[2a	.
=13	=13
2a]	.
2cc	.
2b	.
4a	.
4g	.
=14	=14
2a	.
2g	.
1f	.
=15	=15
0e	-e
=16	=16
0r	.
=17	=17
1b	dum
1dd	.
=18	=18
0cc	fa-
=19	=19
0b	-ta
=20	=20
1e	de-
[1f	-us-
=21	=21
0f]	.
=22	=22
1e	-que
1g	si-
=23	=23
0f	-ne-
=24	=24
0e	-bant,
=25	=25
0g	ac-
=26	=26
1f	-ci-
2e	-pi-
2g	.
=27	=27
2f	-te
1e	hanc
2g	.
=28	=28
4f	a-
4e	.
4d	.
4c	.
1d	-ni-
=29	=29
1c	-mam,
1r	.
=30	=30
1cc	me-
1b	-que
=31	=31
1b	hi-
2a	-is
2g	.
=32	=32
2r	.
2a	ex
2g	sol-
2cc	.
=33	=33
2b	-vi-
1a	.
2g#i	.
=34	=34
1a	-te
1a	cu-
=35	=35
1.dd	.
2cc	.
=36	=36
2b	.
2a	.
2g	.
2f	.
=37	=37
2e	.
2d	.
2g	.
[2f	.
=38	=38
4f]	.
4e	.
1e	.
2d	.
=39	=39
0e	-ris.
=40	=40
[0a	Vi-
=41	=41
0a]	.
=42	=42
0g	-xi
=43	=43
=45	=45
0r	.
=46	=46
0dd	et,
=47	=47
1cc	que
2cc	de-
2cc	-de-
=48	=48
1b	-rat
1a	cur-
=49	=49
0dd	-sum
=50	=50
1r	.
1g	for-
=51	=51
0cc	-tu-
=52	=52
1b	.
[1a	-na,
=53	=53
1a]	.
1g	pe-
=54	=54
1.f#	-re-
4e	.
4f#i	.
=55	=55
1g	-gi,
1r	.
=56	=56
[0c#	et
=57	=57
0c#]	.
=58	=58
[0f	nunc
=59	=59
1f]	.
1d	.
=60	=60
1.g	ma-
4f	.
4e	.
=61	=61
1g	.
1f	.
=62	=62
2e	-gna
1e	me-
2d	.
=63	=63
1e	-i
1r	.
=64	=64
0r	.
=65	=65
[0b	sub
=66	=66
0b]	.
=67	=67
1.cc	ter-
4b	.
4a	.
=68	=68
0g#	-ras
=69	=69
1r	.
1cc	i-
=70	=70
2b	.
2a	.
1g	-bit
=71	=71
2a	i-
2cc	.
2b	.
2a	.
=72	=72
2g	-ma-
2.dd	.
4cc	.
4b	.
4a	.
=73	=73
2g	.
2cc	.
2b	.
2a	.
=74	=74
2g	.
2.a	.
4g#i	.
4g#i	.
4f#i	.
=75	=75
0al	-go.
==	==
*-	*-
</script>


In [VHV](http://verovio.humdrum.org), you can adjust the window size to fit
the music, and then type `alt-t` to download a one-page PDF file of the 
visible music:


{% include image.html
	file="vhvview.png"
	caption="Adjust the windows size to have the music complete fit in view."
%}

Here is the [resulting PDF file](score.pdf), and the PDF file viewed in a PDF viewer:

{% include image.html
	file="score.png"
	caption="Downloaded one-page PDF file in a PDF viewer."
%}



Polyphonic works can also be converted:


{% include verovio.html
	source="example-poly"
	scale="30"
	humdrum-min-width="650"
	tabsize="12"
	pageWidth="1800"
%}

<script type="application/x-humdrum" id="example-poly">

!!!filter: kern2mens -N
**kern	**kern	**kern	**kern
*Ivox	*Ivox	*Ivox	*Ivox
*I"Bassus	*I"Tenor	*I"Altus	*I"Discantus
*I'B	*I'T	*I'A	*I'D
*staff4	*staff3	*staff2	*staff1
*clefF4	*clefC4	*clefC3	*clefC1
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-	=1-
0r	0r	1r	1d
.	.	1G	2d
.	.	.	2d
=2	=2	=2	=2
0r	0r	2G	1g
.	.	2G	.
.	.	1c	2g
.	.	.	[2a
=3	=3	=3	=3
0r	0D	2d	4a]
.	.	.	4g
.	.	4c	4f
.	.	4B	4e
.	.	1A	2.f
.	.	.	4e
=4	=4	=4	=4
0GG	1D	2.G	1g
.	.	4A	.
.	1D	4B	2d
.	.	4c	.
.	.	2d	[2g
=5	=5	=5	=5
1GG	0G	2e	2g]
.	.	1c	4f
.	.	.	4e
1GG	.	.	1d
.	.	2B	.
=6	=6	=6	=6
0C	1r	1.c	1c
.	1G	.	1cc
.	.	4B	.
.	.	4A	.
=7	=7	=7	=7
1r	1B	2G	2.dd
.	.	1g	.
.	.	.	4cc
1C	1c	.	4b
.	.	.	4a
.	.	[2e	[2a
=8	=8	=8	=8
1E	1B	2e]	2a]
.	.	2e	2g
1F	1A	2.c	2a
.	.	.	[2cc
.	.	4d	.
=9	=9	=9	=9
1E	0r	4e	4cc]
.	.	4f	4b
.	.	1g	2g
1D	.	.	1a
.	.	2f#i	.
=10	=10	=10	=10
0r	1B	1g	1d
.	1c	2g	1r
.	.	[2e	.
=11	=11	=11	=11
1E	1B	2e]	1g
.	.	2e	.
1F	1A	2c	2a
.	.	[2d	2a
=12	=12	=12	=12
1E	1B	2d]	1g
.	.	2G	.
1D	1r	1A	1f
=13	=13	=13	=13
1E	1G	1G	2r
.	.	.	2g
1r	1A	[1c	2f
.	.	.	[2e
=14	=14	=14	=14
1C	1G	1c]	2e]
.	.	.	2g
1D	1r	2A	2f
.	.	2B	2d
=15	=15	=15	=15
1C	1E	1c	2g
.	.	.	4f
.	.	.	4e
1r	2F	2r	1d
.	2G	2d	.
=16	=16	=16	=16
1AA	1A	2e	1c
.	.	2c	.
2BB	2r	2d	2f
2C	2G	4c	[2e
.	.	4B	.
=17	=17	=17	=17
1D	1F	1A	2e]
.	.	.	1d
2r	1E	1G	.
2C	.	.	[2g
=18	=18	=18	=18
1BB	1D	2r	4g]
.	.	.	4f
.	.	1G	4e
.	.	.	4d
1AA	1r	.	1c
.	.	2F#i	.
=19	=19	=19	=19
1GG	1d	0G	1r
1r	2d	.	1dd
.	2d	.	.
=20	=20	=20	=20
1G	1B	2r	2dd
.	.	1d	2dd
2G	1G	.	1b
2G	.	[2B	.
=21	=21	=21	=21
1E	1r	2B]	2g
.	.	1e	2.cc
1C	[1c	.	.
.	.	.	4b
.	.	[2e	4a
.	.	.	4g
=22	=22	=22	=22
1r	2c]	2e]	2a
.	2B	2d	2g
[1F	2A	[1c	2a
.	2G	.	[2cc
=23	=23	=23	=23
2F]	0A	1c]	4cc]
.	.	.	4b
2E	.	.	4a
.	.	.	4g
2D	.	2d	2f
2C	.	2e	2g
=24	=24	=24	=24
0D	2D	0d	2f
.	2B	.	1g
.	1A	.	.
.	.	.	2f#i
=25	=25	=25	=25
0GGl	0Gl	0dl	0gl
==	==	==	==
*-	*-	*-	*-


</script>


[But there is currently a bug with polyphonic works that contain text]


See the [while mensural notation](/humdrum/mens) documentation page for more information
about the `**mens` representation.




