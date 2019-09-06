---
title: imitation filter
lang: en
ref: filters-imitation
author: "Craig Sapp"
translator: 
creation_date: 18 Jun 2017
translation_date: 
last_updated: 18 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "The imitation filter identifies modal melodic repetition between voices."
permalink: /filters/imitation/index.html
---

The imitation tool identifies repeated interval patterns between
voices.  The following example demonstrate the results from the
tool for the opening two voices of the first fugue from J.S. Bach's
Well-tempered Clavier, Book I (BWV 846).


{% include verovio.html
	source="wtc1f01m1t4"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="wtc1f01m1t4">
!!!filter: imitation
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

Try changing pitches in the textual music on the left to see how
the matches change.


## Imitation summary ##

Beneath the first note of each imitation pair, a text string gives
four pieces of information about the imitation.  The four fields
are separated by colons, and each value is prefixed by a letter:

prefix | parameter meaning
=======|=================
n      | A unique enumeration ID for each imitation pairs within the score, starting at 1.
c      | The note *count* in each the imitation pairing.
d      | The *distance* (duration) between the first note in each imitation pair.  A positive value means that the imitation occurs after the current sequence, while a negative value means that the other imitation sequence comes before the current sequence.
i      | The imitation *interval* in diatonic steps.  Positive values means the imitation in the other location is higher in pitch than the current sequence, while a negative value means that the paired sequence is at a lower pitch.


So the text under the first note in the above example (`n1:c14:d6:i5`) means that
this is the first pair, where there are 14 shared notes (13 intervals), the imitation
is at the fifth, and the distance between the sequence starts is 6 quarter notes.

## Suppressing information ##

There are several options to modify the display of the match information.  To completely suppress the 
matching information, use the `-q` option (meaning "quiet"):


{% include verovio.html
	source="quiet"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="quiet">
!!!filter: imitation -q
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


The matches are still highlighted, but no textual information is added to the score.  You can also selectively 
remove the `n`, `c`, `d` or `i` fields by adding the option `-N`, `-C`, `-D` or `-I` respectively.  Here is an example of 
removing the count and distance and fields at the same time:


{% include verovio.html
	source="nocd"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nocd">
!!!filter: imitation -CD
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


Information can be suppressed from the second sequence in the match by using the `-f` option, meaning give only
the information on the "first" sequence in the pair:


{% include verovio.html
	source="first"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="first">
!!!filter: imitation -f
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


The options `--NN`, `--CC`, `--DD`, and `--II` can selectively suppress match fields from the 
second match.  Here is an example showing only the `n` field on the second pair of a match:


{% include verovio.html
	source="nonly"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nonly">
!!!filter: imitation --CC --DD --II
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


The `-2` option is a shortcut for `--CC --DD --II`:


{% include verovio.html
	source="nonly2"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nonly2">
!!!filter: imitation -2
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


## Adding information ##

The `-m` option can be used to add measure numbers to the match information, and `-b` can add the
beat information.  The beat information is actually in units of quarter notes (regardless of the
meter), with the first beat of a measure labeled as beat "1".

{% include verovio.html
	source="measure"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="measure">
!!!filter: imitation -mb
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

The `-l` (lower-case L), can be used to enclude the length of the matched sequence:

{% include verovio.html
	source="length"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="length">
!!!filter: imitation -l
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


The length is prefixed by the letter `L` in the information string.  In this case
the length of both matches is 5.75 quarter notes.



## Note count threshold ##

The `-t` option is used to set a threshold number of notes that must be matched.  The default number of notes is 7.  In the
example music, there are 14 notes that match between the two fugal entrances, so if the threshold is set to 15, this pair
will not be identified:


{% include verovio.html
	source="threshold"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="threshold">
!!!filter: imitation -t 15
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

But setting the threshold to 14 will result in a match:


{% include verovio.html
	source="threshold14"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="threshold14">
!!!filter: imitation -t 14
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


## Maximum distance between imitation ##

The `-d` option can be used to limit the distance (duration) between
matches.  This is useful for highlighting imitative entries while
minimizing matching noise.  By default, any duration between matches
is allowed.  To limit the search distance between matches specify
the maximum duration between pairs in units of quarter notes.  Below
is an example limiting the match distance to 4 quarter notes.  Since
the distance between the fugal entrances is 6 quarter notes, so no
match is identified:


{% include verovio.html
	source="distance4"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="distance4">
!!!filter: imitation -d 4
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>


Increasing the minimum distance to 6 quarter notes or more will catch the imitation:

{% include verovio.html
	source="distance6"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="distance6">
!!!filter: imitation -d 6
**kern	**kern
*clefG2	*clefG2
*k[]	*k[]
*C:	*C:
*M4/4	*M4/4
*MM62	*MM62
=1	=1
8r	1r
8cL	.
8d	.
8eJ	.
8.fL	.
32g	.
32fJ	.
8eL	.
8aJ	.
=2	=2
8dL	2r
[8gJ	.
16g]L	.
16a	.
16g	.
16fJ	.
16eL	8r
16f	.
16e	8gL
16dJ	.
16cL	8a
16d	.
16c	8bJ
16BJ	.
=3	=3
8AL	8.ccL
8f#J	.
.	32dd
.	32ccJ
[4g	8bL
.	8eeJ
8g]L	8aL
16f#	[8ddJ
16eJ	.
8f#L	16dd]L
.	16ee
8dJ	16dd
.	16ccJ
=4	=4
8gL	16bL
.	16g
8fnJ	16a
.	16bJ
8eL	16ccL
.	16b
8dJ	16cc
.	16ddJ
8c	16eeL
.	16dd
8r	16ee
.	16ff#J
8r	8ggL
8ryy	8bJ
=	=
*-	*-
</script>

## Imitation by pitch but not by rhythm ##

The `-p` option will consider only pitches when searching for matches, ignoring 
the durations of the notes.  Here is an example match between two sequences
that have the same notes in sequence, but the rhythms are different:


{% include verovio.html
	source="pitch"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="pitch">
!!!filter: imitation -p
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	1r
4d	.
4e	.
4f	.
=2	=2
4g	8.cL
.	16dJ
4a	8.eL
.	16fJ
4b	8gL
.	8a
4cc	8b
.	8ccJ
=	=
*-	*-
</script>


## Matching inversions ##

The `-v` option can be used to match inversions.  Here is an example where an upward and downward scale are 
matched to each other:


{% include verovio.html
	source="inversion"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="inversion">
!!!filter: imitation -v
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	2r
4d	.
4e	4cc
4f	4b
=2	=2
4g	4a
4a	4g
4b	4f
4cc	4e
2r	4d
.	4c
=	=
*-	*-
</script>

Notice that the enumeration number is prefixed by `v` to indicate that the imitation 
relation in an inversion.  The interval value indicates the interval between the first
pair of notes in the two sequences.

Adding the `-a` option to the `-v` option will search for both regular matches as well
as inversion matches at the same time.  Here is an example:

{% include verovio.html
	source="add"
	spacingStaff="8"
	scale="35"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="add">
!!!filter: imitation -av
**kern	**kern
*M4/4	*M4/4
=1	=1
4c	8cL
.	8eJ
4d	8gL
.	8ccJ
4e	8bL
.	8ddJ
4f	4cc
=2	=2
4g	4b
4a	4a
4b	4g
4cc	4f
=3	=3
8cL	4e
8eJ	.
8gL	4d
8ccJ	.
8bL	4B
8ddJ	.
4cc	4c
=	=
*-	*-
</script>

Each type of search will be given a different color (but only one color can be
displayed when the match types overlap).


## Selecting or avoiding parallel motion ##

The '-z' option can be used to select only imitation that starts at the same time.
This is an alias for `-d 0`:


{% include verovio.html
	source="parallel"
	spacingStaff="8"
	scale="35"
	pageWidth="1450"
	tabsize="10"
%}
<script type="application/x-humdrum" id="parallel">
!!!filter: imitation -z
**kern	**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M4/2	*M4/2	*M4/2	*M4/2
=34	=34	=34	=34
4c	4f	0r	1r
8BL	4e	.	.
8cJ	.	.	.
4d	2.d	.	.
4c	.	.	.
4B	.	.	2r
4e	4c	.	.
2d	2B	.	[2g
=35	=35	=35	=35
2c	4e	4r	4g]
.	2c	2e	4a
2r	.	.	4g
.	4d	4f	8fL
.	.	.	8gJ
1r	4c	4e	4a
.	8BL	8dL	4g
.	8cJ	8eJ	.
.	4d	4f	[2f
.	4c	4e	.
=36	=36	=36	=36
1r	4B-X	4d	4f]
.	4G	4d	4g
.	2A	2c#X	2e
2r	2A	4d	2d
.	.	4d	.
2A	2d	[2f	4r
.	.	.	4a
=37	=37	=37	=37
2D	2d	2f]	2b-X
2G	2c	2e	2g
4F	4c	4f	4a
4G	4c	4e	4g
4G	4c	4.e	4g
4c	4e	.	4a
.	.	8f	.
=	=	=	=
*-	*-	*-	*-
</script>



The '-Z' option will do the opposite: remove any imitation pairs that start at the same time:


{% include verovio.html
	source="noparallel"
	spacingStaff="8"
	scale="35"
	pageWidth="1450"
	tabsize="10"
%}
<script type="application/x-humdrum" id="noparallel">
!!!filter: imitation -Z
**kern	**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M4/2	*M4/2	*M4/2	*M4/2
=34	=34	=34	=34
4c	4f	0r	1r
8BL	4e	.	.
8cJ	.	.	.
4d	2.d	.	.
4c	.	.	.
4B	.	.	2r
4e	4c	.	.
2d	2B	.	[2g
=35	=35	=35	=35
2c	4e	4r	4g]
.	2c	2e	4a
2r	.	.	4g
.	4d	4f	8fL
.	.	.	8gJ
1r	4c	4e	4a
.	8BL	8dL	4g
.	8cJ	8eJ	.
.	4d	4f	[2f
.	4c	4e	.
=36	=36	=36	=36
1r	4B-X	4d	4f]
.	4G	4d	4g
.	2A	2c#X	2e
2r	2A	4d	2d
.	.	4d	.
2A	2d	[2f	4r
.	.	.	4a
=37	=37	=37	=37
2D	2d	2f]	2b-X
2G	2c	2e	2g
4F	4c	4f	4a
4G	4c	4e	4g
4G	4c	4.e	4g
4c	4e	.	4a
.	.	8f	.
=	=	=	=
*-	*-	*-	*-
</script>



