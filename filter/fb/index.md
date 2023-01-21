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


## Selective analysis ##

In addition to calculating the numbers of all `**kern` spines in a
file, the `fb` filter can select a subset of the music to be analyzed.
Spines can be selected either by using `-s` to select the nth spine in
the file, or with `-k` to select the nth `**kern` spine in the file.


### Selecting spines with -s ###


| Example        | Meaning                                                                          |
|----------------|----------------------------------------------------------------------------------|
| `-s 1`         | Analyze only the first (leftmost) spine in the input data.                       |
| `-s 1,4`       | Analyze the first and fourth spine.                                              |
| `-s 2-4`       | Analyze the second, third and fourth spines.                                     |
| `-s $`         | Analyze the last spine.                                                          |
| `-s 3,$`       | Analyze the thrid and last spines.                                               |
| `-s 1-4,6,9-$` | Analyze the first, second, third, fourth, sixth, and nineth through last spines. |
| `-s $1`        | Analyze the penultimate spine.                                                   |
| `-s $2-$`      | analyze from two spines before the end to the last spine.                        |



### Selecting spines with -k ###

| Example        | Meaning                                                                               |
|----------------|---------------------------------------------------------------------------------------|
| `-k 1`         | Analyze only the first (leftmost) kern spine in the input data.                       |
| `-k 1,4`       | Analyze the first and fourth kern spine.                                              |
| `-k 2-4`       | Analyze the second, third and fourth kern spines.                                     |
| `-k $`         | Analyze the last kern spine.                                                          |
| `-k 3,$`       | Analyze the thrid and last kern spines.                                               |
| `-k 1-4,6,9-$` | Analyze the first, second, third, fourth, sixth, and nineth through last kern spines. |
| `-k $1`        | Analyze the penultimate kern spine.                                                   |
| `-k $2-$`      | analyze from two kern spines before the end to the last kern spine.                   |



## Place numbers above the staff ##

By default numbers will be displayed below the staff when shown in a
musical score. You can add the `--above` option to show them above the
staff.

{% include verovio.html
	source="above_f"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="above_f">
!!!filter: fb -f --above
**kern	**kern
*clefF4	*clefG2
4F	4d 4g 4b
4E	4e 4g 4cc
4D	4f 4b 4dd
4C	4g 4cc 4ee
=	=
*-	*-
</script>

This also works when using the `-i` option.

{% include verovio.html
	source="above_i"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="above_i">
!!!filter: fb -i --above
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



## *Intervallsatz* ##

When working e.g. with polyphonic renaissance music the
*Intervallsatz* option `-i` (`--intervallsatz`) is the best way to
display the numbers of each voice directly under it's staff. This is a
good way for students to get a fast overview over the intervals and
check for possible dissonant or parallel intervals. Recommended
options are in combination with `-i -c -a -t -m`.

{% include verovio.html
	source="intervallsatz"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="intervallsatz">
!!!filter: fb -i
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

When passing the `-t` option (`--ties`) in combination with `-i`
numbers without attack or changing base note can be hidden.

{% include verovio.html
	source="ties"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="ties">
!!!filter: fb -i -t
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



## Control the frequency of the numbers ##

By default `fb` will calculate number for every single slice (=line).
You can controll this by passing the option `--frequency` with a
rhythmical value for a note duration (compare with `recip`). With this
options you can tell `fb` to only display numbers on every quarter
note.

{% include verovio.html
	source="frequency"
	humdrum-min-height="275px"
	scale="40"
	tabsize="8"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="frequency">
!!!filter: fb -n --frequency 4
**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#c#]	*k[f#c#]	*k[f#c#]	*k[f#c#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
=1-	=1-	=1-	=1-
8BL	4d	4f#	4b
8AJ	.	.	.
4G	8c#L	4e	4b
.	8BJ	.	.
8F#L	4c#	4f#	4a
8E	.	.	.
8D	4B	8f#L	4dd
8BBJ	.	16gL	.
.	.	16aJJ	.
=2	=2	=2	=2
8EL	4.B	8gL	8cc#L
8D	.	8f#J	8bJ
8E	.	4e	4cc#
8F#J	8A#	.	.
2BB;	2F#;	2d;	2b;
=3	=3	=3	=3
*-	*-	*-	*-
</script>

This option is particularly useful when the metre is ternary, e.g.
*six-eighths* or *nine-eighths*.

{% include verovio.html
	source="frequency98"
	humdrum-min-height="275px"
	scale="35"
	tabsize="8"
	pageWidth="1500"
%}
<script type="application/x-humdrum" id="frequency98">
!!!filter: fb -n --frequency 4.
**kern	**kern
*k[b-]	*k[b-]
*M9/8	*M9/8
(8FF'L 8C 8F 8A	4.s
8FF' 8C 8F 8A	.
8FF'J 8C 8F 8A	.
8FF'L 8C 8F 8A	4.s
8GG' 8C 8E 8G	.
8FF'J 8C 8F 8A	.
8EE'L 8C 8G 8B-	(8c
8EE' 8C 8F 8A	8d
8EE'J 8C 8E 8B-)	8c)
=	=
(8FF' 8C 8F 8A	[4.a
8FF' 8C 8F 8A	.
8FF' 8C 8F 8A	.
8FF' 8C 8F 8A	8a]
8FF' 8C 8F 8A	(8b-'
8FF' 8C 8F 8A	8b')
8FF' 8C 8F 8A	(8cc
8FF' 8C 8F 8A	8a)
8FF' 8C 8F 8A)	8f'
=	=
8BB- 8F 8B-	(4.e
8BB- 8F 8B-	.
8BB- 8F 8B-	.
8BB- 8F 8B-	4.d)
8BB- 8F 8B-	.
8BB- 8F 8B-	.
8AA 8C 8F 8B-	(4d
8AA 8C 8F 8B-	.
8AA 8C 8F 8B-	8c)
=	=
*-	*-
!!!filter: autobeam
</script>
