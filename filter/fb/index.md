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
