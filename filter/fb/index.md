---
title: fb filter
lang: en
ref: filters-fb
author: Wolfgang Drescher
translator: 
creation_date: 17 Jan 2023
translation_date: 
last_updated: 21 Jan 2023
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/fb/index.html
---

The `fb` filter analyzes the harmonies in `**kern` data and reduces
them to figured bass like numbers. There are different modes of how
the numbers can be displayed. This filter supports chords as well as
spine splits. The reference note for the calculations is in each case
the lowest pitch within the base track that can be passed with the
`--base` option.

Here is a basic example:

{% include verovio.html
	source="basic"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="basic">
!!!filter: fb -f
**kern	**kern
*clefF4	*clefG2
4F	4d 4g 4b
4E	4e 4g 4cc
4D	4f 4b 4dd
4C	4g 4cc 4ee
=	=
*-	*-
</script>

If you do not pass any additional options `fb` will calculate the
interval of the distance between the base voice (defualt is the first
`**kern` spine) and each note that occurs in a single slice of music
(which corresponds to one line of the file in humdrum).

{% include verovio.html
	source="fb"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="fb">
!!!filter: fb
**kern	**kern
*clefF4	*clefG2
4c	4gg
4c	4ff
4c	4ee
4c	4dd
4c	4cc
4c	4b
4c	4a
4c	4g
4c	4f
4c	4e
4c	4d
4c	4c
=	=
*-	*-
</script>



## Compound intervals ##

By default, `fb` will display the exact distance between the target
and base note as compound intervals. If you want to display the
numbers 2-7 as non-compound intervals reduced with an octave you can
use the `-c` option (`--compound`) to do so. This is similar to the
`-c` option of the `hint` command in the Humdrum Toolkit. When `-c` is
used in combination with `-i`, 1 is displayed for a unison.

{% include verovio.html
	source="compound"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="compound">
!!!filter: fb -c
**kern	**kern
*clefF4	*clefG2
4c	4gg
4c	4ff
4c	4ee
4c	4dd
4c	4cc
4c	4b
4c	4a
4c	4g
4c	4f
4c	4e
4c	4d
4c	4c
=	=
*-	*-
</script>



## Accidentals ##

By default, `fb` will not display any accidentals. Use the `-a` option
(`--accidentals`) to display naturals, sharps and flats infront of the
numbers.

{% include verovio.html
	source="accidentals"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="accidentals">
!!!filter: fb -c -a
**kern	**kern
*clefF4	*clefG2
4c	4cc
4c	4bn
4c	4a#
4c	4g-
4c	4f##
4c	4e--
4c	4d
4c	4c
=	=
*-	*-
</script>

The display of naturals, sharps and flats depends on the current key
signature:

{% include verovio.html
	source="keysig"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="keysig">
!!!filter: fb -a
**kern	**kern
*clefF4	*clefG2
*k[b-e-a-]	*k[b-e-a-]
4c	4a#
4c	4a
4c	4a-
4c	4g#
4c	4g
4c	4g-
=	=
*k[f#c#g#]	*k[f#c#g#]
4c	4a#
4c	4a
4c	4a-
4c	4g#
4c	4g
4c	4g-
=	=
*-	*-
</script>

You can hide the number 3 with the option `-3` (`--hide-three`) if the
display is not necessary because of an existing accidental.

{% include verovio.html
	source="hide3"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="hide3">
!!!filter: fb -a -3
**kern	**kern
*clefF4	*clefG2
4c	4e#
4c	4e
4c	4e-
=	=
*k[b-e-]	*k[b-e-]
4c	4e#
4c	4e
4c	4e-
=	=
*k[f#c#g#d#a#e#]	*k[f#c#g#d#a#e#]
4c	4e#
4c	4e
4c	4e-
=	=
*-	*-
</script>



## Negative intervals ##

By default, `fb` will ignore intervals if they are below the pitch of
the base track. You can change this behaviour by adding an option `-m`
(`--negative`). This is especially interesting in combination with the
option `-i`, for example in renaissance music, when there is an voice
exchange. 

{% include verovio.html
	source="neg"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="neg">
!!!filter: fb -m
**kern	**kern
*clefC3	*clefC3
4c	4g
4c	4f
4c	4e
4c	4d
4c	4c
4c	4B
4c	4A
4c	4G
=	=
*-	*-
</script>



## Lowest pitch as base ##

With the `-l` option (`--lowest`) you can let `fb` find the lowest
pitch of each slice and use this note as base for all number
calculations. This options will ignore a potentially passend base
track with `-b`.

{% include verovio.html
	source="lowest"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="lowest">
!!!filter: fb -c -l
**kern	**kern
*clefF4	*clefG2
4G	4b 4dd
4B	4G 4dd
=	=
*-	*-
</script>



## Base track ##

By default, `fb` will use the first `**kern` spine as base track. But
you can change this behaviour by using the `-b` option (`--base`).
Valid values are numbers of the desired base `**kern` spine (compare
to `-k`). This is especially useful in combination with `-i -m`.

{% include verovio.html
	source="base"
	humdrum-min-height="275px"
	scale="35"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="base">
!!!filter: fb -i -m -b 3
**kern	**kern	**kern
*clefG2	*clefG2	*clefG2
*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=1	=1	=1
2r	1b-	2r
2B-	.	2dd
2G	2b-	2dd
2A	2a	2cc#
=2	=2	=2
2B	2g	2dd
2c	2g	2ee
2d	1f#	1a
2d	.	.
=	=	=
*-	*-	*-
</script>
