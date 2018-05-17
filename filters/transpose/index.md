---
transpose: transpose filter
author: Craig Stuart Sapp
creation_date: 23 Apr 2017
last_updated: 23 Apr 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filters/transpose/index.html
---

The transpose filter can be used transpose music by a specified
interval or to a specific key.

## Transposing by key ##

Here is an example of transposing a four-part chorale
from G major to A-flat major, using the `-k` option to change
the key:

```
!!!filter: transpose -k a-
```

{% include verovio.html
	source="chorale"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="chorale">
!!!filter: transpose -k a-
**kern	**kern	**kern	**kern
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*G:	*G:	*G:	*G:
*M3/4	*M3/4	*M3/4	*M3/4
4GG	4B	4d	4g
=1	=1	=1	=1
4G	4B	4d	2g
4E	8cL	4e	.
.	8BJ	.	.
4F#	4A	4d	4dd
=2	=2	=2	=2
4G	4G	2d	4.b
4D	4F#	.	.
.	.	.	8a
4E	4G	4B	4g
=3	=3	=3	=3
4C	8cL	8eL	4.g
.	8BJ	8d	.
8BBL	4c	8e	.
8AAJ	.	8f#J	8a
4GG	4d	4g	4b
=4	=4	=4	=4
2D;	2d;	2f#;	2a;
4GG	4d	4g	4b
=5	=5	=5	=5
4FF#	4A	4d	2dd
4GG	4B	4e	.
4AA	4c	4f#	4cc
=6	=6	=6	=6
4BB	4d	2g	4b
4C	4e	.	2a
4D	8dL	4f#	.
.	8cJ	.	.
=7	=7	=7	=7
2GG;	2B;	2d;	2g;
=:|!	=:|!	=:|!	=:|!
4GG	4d	[4g	4b
=8	=8	=8	=8
4GG	4d	8gL]	4b
.	.	8f#J	.
4AA	4c	8eL	4cc
.	.	8f#J	.
4BB	8BL	[4g	4dd
.	8AJ	.	.
=9	=9	=9	=9
4.BB	8BL	8gL]	4.dd
.	8cJ	8aJ	.
.	4d	8gL	.
8AA	.	8f#J	8cc
4GG	4d	4g	4b
=10	=10	=10	=10
2D;	2d;	2f#;	2a;
[4E	4B	4e	4g
=11	=11	=11	=11
4E]	4G	4e	2b
4D	4B	8f#L	.
.	.	8gJ	.
4C	4e	4a	4cc
=12	=12	=12	=12
4.BB	2d	4a	2dd
.	.	4.g	.
8C	.	.	.
4D	4d	.	4cc
.	.	8f#	.
=13	=13	=13	=13
8GGL	2.d	2g	2.b
8AAJ	.	.	.
4BB	.	.	.
4GG	.	4f	.
=14	=14	=14	=14
2C;	2c;	2e;	2g;
4GG	4d	4g	4b
=15	=15	=15	=15
4FF#	8dL	4.a	2dd
.	8cJ	.	.
4GG	4B	.	.
.	.	8g	.
4AA	4c	4f#	4cc
=16	=16	=16	=16
4BB	2d	2g	2b
4GG	.	.	.
4D	8dL	[4f#	4a
.	8cJ	.	.
=17	=17	=17	=17
8EL	4B	8f#L]	4.g
8D	.	8eJ	.
8C	4c	8eL	.
8BB	.	8f#J	8a
8AA	4d	4g	4b
8GGJ	.	.	.
=18	=18	=18	=18
2D;	2d;	2f#;	2a;
[4G	4d	4g	4b
=19	=19	=19	=19
4G]	2d	2a	2dd
4F#	.	.	.
[4E	4e	8gL	4cc
.	.	8f#J	.
=20	=20	=20	=20
8EL]	2e	2g	4b
8DJ	.	.	.
4C	.	.	2a
4D	8dL	4f#	.
.	8cJ	.	.
=21	=21	=21	=21
2GG;	2B;	2d;	2g;
==	==	==	==
*-	*-	*-	*-
</script>

Try changing `a-` to `a` on the first line of the example to transpose 
to A major instead.

The transpose filter is identical to the Humdrum Extras command-line tool
[transpose](http://extras.humdrum.org/man/transpose).  See its documentation for
more examples of how to use the transpose filter.

## Transposing by musical interval ##

The `-k` option requires a key interpretation present in the data, such
as `*C:` for C major, or `*b-:` for B-flat minor.  If this is not then case,
then you can still transpose by a specific interval using the `-t` option.

Transposing down a major third: `!!!filter: transpose -t -M3`

Transposing down a minor sixth: `!!!filter: transpose -t m6`

Transposing down a perfect fourth: `!!!filter: transpose -t -P4`

Transposing up a diminished fifth: `!!!filter: transpose -t d5`

Transposing down an augmented unison, such as from E major to E-flat 
major: `!!!filter: transpose -t -A1`

Try various interval transpositions in the following example, which 
starts out in the key of C major (but there is no key indication, so
the `-k` option cannot be used).

{% include verovio.html
	source="transpose"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="transpose">
!!!filter: transpose -t M2
**kern
4c
4d
4e
8fL
8f#J
4g
4aL
4a-J
4b
4cc
==
*-
</script>

## Transposing by base-40 interval number ##

The Base-40 representation for pitches allows for integer values for
various intervals.  All of these interval numbers can be calculated
from two pieces of information: A major second is a 6 in the system,
and a minor second is a 5.  For example a perfect fifth is composed of
three major seconds and one minor second, so the base-40 interval is 3 *
6 + 1 * 5 = 23.  An octave is 5 major seconds and 2 minor seconds, which
translates to 5 * 6 + 2 * 5 = 40 (hence the name of the system).  Note
that an augmented unison is the difference between a major and minor second,
which is 1.

Try transposing the following example by base-40 interval, which is 
given as an integer after the `-b` option flag in the transpose 
filter. Also note that the base-40 system is limited to a range of
double-flats to double-sharps, so intervals that transpose to/by 
triple-flats will not work in the system.

{% include verovio.html
	source="base40"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}

<script type="application/json" id="base40">
!!!filter: transpose -b 6
**kern
4c
4d
4e
8fL
8f#J
4g
4aL
4a-J
4b
4cc
==
*-
</script>



## `**mxhm` transposition ##

Chord symbols imported from MusicXML are stored in an `**mxhm` spine.
These symbols are understood by the transpose tool and will be transposed
along with any `**kern` spines in the data.

Below is an example work containing an `**mxhm` data spine.  The original
key is C major, but the transpose tool is changing the key of the piece
to D major.  Try transposing the music to other keys by changing the
`d` on the first line of the text box below to another tonic pitch.


{% include verovio.html
	source="muss"
	scale="40"
	pageWidth="1250"
	tabsize="10"
%}

<script type="application/json" id="muss">
!!!filter: transpose -k d
**kern	**mxhm
*part1	*part1
*staff1	*
*clefG2	*
*k[]	*
*C:	*C:
*M4/4	*
=1-	=1-
2r	.
!!LO:TX:a:t=N.C.
4c	.
4d	.
=2!|:	=2!|:
2e	C major
4e	.
4g	.
=3	=3
2f	G dominant
4f	.
4a	.
=4	=4
4.g	C major
8a	.
4g	.
4f	.
=5	=5
1e	.
=6	=6
4.g	.
8a	.
4g	.
4f	.
=7	=7
2e	.
4e	.
4g	.
=8	=8
2f	D minor
4f	.
4e	.
=9	=9
2d	G dominant
2g	.
=10	=10
[1e	C major
=11	=11
2e]	.
!!LO:TX:a:t=N.C.
4c	.
4d	.
=12:|!	=12:|!
2d	G dominant
2e	.
=13	=13
[1c	C major
=14	=14
2c]	F major
4c	C major
!!LO:TX:a:t=N.C.
4e	.
=15	=15
2.d	D minor
4e	.
=16	=16
2.f	G dominant
4d	.
=17	=17
2.e	C major
4f	.
=18	=18
2g	C dominant
4g	.
4g	.
=19	=19
2a	F major
2a	.
=20	=20
2cc	.
4b	.
4a	.
=21	=21
[1g	C major
=22	=22
2g]	G dominant
!!LO:TX:a:t=N.C.
4c	.
4d	.
=23	=23
2e	C major
4e	.
4g	.
=24	=24
2f	G dominant
4f	.
4a	.
=25	=25
4.g	C major
8a	.
4g	.
4f	.
=26	=26
2.e	.
4e	.
=27	=27
4.g	.
8a	.
4g	.
4f	.
=28	=28
2e	.
4e	.
4g	.
=29	=29
2f	D minor
4f	.
4e	.
=30	=30
2d	G dominant
2e	.
=31	=31
[1c	C major
=32	=32
2c]	F major
2r	C major
==	==
*-	*-
</script>




