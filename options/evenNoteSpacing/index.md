---
title: Maximally compressed notation
lang: en
ref: verovio options evenNoteSpacing
author: Craig Stuart Sapp
creation_date: 2 May 2022
translator: 
translation_date: 
last_updated: 2 May 2022
tags: [all, options]
sidebar: main_sidebar
verovio: "true"
keywords: embedded verovio options evenNoteSpacing
vim: ts=3
summary: 
permalink: /options/evenNoteSpacing/index.html
---

The `evenNoteSpacing` verovio option is useful to compress the
musical spacing in order to see more music on the screen.  This
is useful for viewing analysis results.

Also see [comprehensive list of options](/options/list).

Example without the `evenNoteSpacing` option:

{% include verovio.html
	humdrum-min-height="400px"
	source="optionoff"
	tabsize="8"
	scale="30"
	pageWidth="1800"
%}
<script type="application/x-humdrum" id="optionoff">
!!!filter: synco
**kern	**kern	**kern
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
</script>


{% include verovio.html
	humdrum-min-height="400px"
	source="optionon"
	tabsize="8"
	scale="30"
	pageWidth="1800"
%}
<script type="application/x-humdrum" id="optionon">
!!!verovio: evenNoteSpacing
!!!filter: synco
**kern	**kern	**kern
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
</script>


## Equivalent spacing options ##

The `evenNoteSpacing` option is a shortcut for two other options:

```
!!!verovio: spacingLinear 0.0
!!!verovio: spacingNonLinear 0.0
```

To compress the musical spacing in a less drastic manner that `evenNoteSpacing`
does, try setting these options to a non-zero value.  Here are the default
spacing parameters:

```
!!!verovio: spacingLinear 0.25
!!!verovio: spacingNonLinear 0.60
```

The `spacingLinear` option is used to control the compression of the notation,
while the `spacingNonLinear` is used to control the relative spacing between
rhythmic levels.  For example, a value of 1.0 for `spacingNonLinear` means that
the half-note takes the same space as two quarter notes.  A value of 0.4 is
approximately gives an equivalent spacing for the quarter and half notes.

Here are settings that produce music with 1/2 the space as the original
example:

```
!!!verovio: spacingLinear 0.30
!!!verovio: spacingNonLinear 0.45
```

{% include verovio.html
	humdrum-min-height="400px"
	source="optiondual"
	tabsize="8"
	scale="30"
	pageWidth="1800"
%}
<script type="application/x-humdrum" id="optiondual">
!!!verovio: spacingLinear 0.30
!!!verovio: spacingNonLinear 0.45
!!!filter: synco
**kern	**kern	**kern
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
</script>



