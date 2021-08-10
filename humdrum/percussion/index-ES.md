---
title: Percussion
lang: en es
ref: humdrum-tuplet_styling
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum percussion
creation_date: 11 Oct 2020
translation_date: 10 Aug 2021
last_updated: 11 Oct 2020
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Encoding methods for percussion parts.
sidebar: main_sidebar
permalink: /humdrum/percussion/index-ES.html
---

Percussion parts are encoded in `**kern` spines, using a percussion
clef and markers to indicate unpitched or semipitched notes, as
well as interpretation or layout parameter control of notehead shapes.

## Percussion clef ##

Use `*clefX` for a percussion clef, with `X` meaning unpitched.

{% include verovio.html
	source="xclef"
	pageWidth="1450"
	scale="60"
	humdrum-height="105"
	humdrum-min-height="105"
%}
<script type="application/json" id="xclef">
**kern
*clefX
*M4/4
1bR
*-
</script>

If a number is given after `X`, the clef will be centered on that line.

{% include verovio.html
	source="xclef5"
	pageWidth="1450"
	scale="60"
	humdrum-height="105"
	humdrum-min-height="105"
%}
<script type="application/json" id="xclef5">
**kern
*clefX5
*M4/4
1bR
*-
</script>





## Staff lines ##

To set the number of lines for a staff, add the interpretation
`*stria` at the start of the spine before any data (notes/rests),
adding the number of lines at the end of the interpretation. 

{% include verovio.html
	source="stria1"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="stria1">
**kern
*stria1
*clefX
*M4/4
4eR
8eRL
8eRJ
8eR/L
8eR/J
4eR/
*-
</script>


## Unpitched notes ##

The placement of notes on the staff is controlled by assigning pitch
names to the notes, and they will be positioned as if they were on
a treble-clef staff.  If there is a single line on the staff, then
that is treated as the bottom line of the treble clef, and the notes
placed on this line have the "pitch" of `e`.

Percussion notes must include `R` to indicate that they are
unpitched.  This is important for analysis purposes, so percussion-clef
notes without an `R` qualification will be highlighted in red to indicate
a problem:

{% include verovio.html
	source="unpitched"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="unpitched">
**kern
*stria1
*clefX
*M4/4
4e
8eL
8eJ
8eR/L
8eR/J
4eR/
*-
</script>

## Partially pitched notes ##

If notes are not pitched, but also not fully unpitched, the marker
`RR` can be used to indicate that a note is partially pitched.  This
is useful for instruments such as tom-toms or <a target="_blank"
href="https://www.youtube.com/watch?v=7otWy6LcaRA">rototoms</a>
where the drums are pitched from low to high.  In this case the
general pitch-height is useable for analysis rather than the notated
pitch.


{% include verovio.html
	source="semipitched"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="215"
%}
<script type="application/json" id="semipitched">
**kern
*clefX
*M4/4
4eRR
8gRRL
8ffRRJ
8ddRR/L
8dRR/J
4gRR/
*-
</script>

## Notehead shapes ##

Notehead shapes can be set either by layout parameters applied to
individual notes, or a notehead shape interpretation that affects
all notes after it in the music.  Available notehead shapes:

| shape   | description |
| ------- | ----------- |
| x       | notehead shaped like an "x" |
| plus    | notehead shaped like a plus sign |
| dia     | notehead shaped like a diamond |
| slash   | slash chord notehead shape |
| solid   | notehead shape of quarter notes and shorter |
| open    | notehead shaped like a half note |
| whole   | notehead shaped like a whole-note |
| regular | regular notehead shape |


### Layout parameter  method ###

Add a note layout parameter immediately before the note with
a "head" parameter set to the notehead shape:

{% include verovio.html
	source="shape1"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="400"
%}
<script type="application/json" id="shape1">
**kern
*stria1
*clefX
=1
!LO:N:head=x
4eR
!LO:N:head=plus
4eR
!LO:N:head=dia
4eR
!LO:N:head=slash
4eR
!LO:N:head=solid
4eR
!LO:N:head=open
4eR
!LO:N:head=whole
4eR
!LO:N:head=regular
4eR
*-
</script>


### Interpretation method ###

If the notehead shape does not change often, use the `*head` interpretation:

{% include verovio.html
	source="shape2"
	pageWidth="1450"
	scale="60"
	humdrum-min-height="350"
%}
<script type="application/json" id="shape2">
**kern
*stria3
*clefX
*M4/4
*head:x
4eR/
8gR/L
8bR/J
8bR/L
8eR/J
4gR/
*head:dia
16bRL
16aR
16gR
16fRJ
4eR
*-
</script>

## Rests ##

Rests will usually be centered on staff lines:


{% include verovio.html
	source="rest1"
	pageWidth="1450"
	humdrum-max-height="150"
	scale="45"
	humdrum-min-width="350"
%}
<script type="application/json" id="rest1">
**kern	**kern	**kern	**kern	**kern
*stria5	*stria4	*stria3	*stria2	*stria1
*clefX	*clefX	*clefX	*clefX	*clefX
1r	1r	1r	1r	1r
2r	2r	2r	2r	2r
4r	4r	4r	4r	4r
8r	8r	8r	8r	8r
16r	16r	16r	16r	16r
=	=	=	=	=
*-	*-	*-	*-	*-
</script>


Since rests are not pitched, there is no need to add `R` markers that
are needed for unpitched sounding notes.


To move rests vertically, add the treble-clef pitch for the desired position
on the staff, where the lowest line of the percussion clef is `e`:


{% include verovio.html
	source="rest2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="245"
%}
<script type="application/json" id="rest2">
**kern
*stria3
*clefX
8r
8rc
8re
8rg
8rb
8rdd
=
*-
</script>


## Transposition ##

Unlike pitched notes, unpitched notes will not be transposed by the transpose filter:


{% include verovio.html
	source="transpose1"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose1">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

Applying the filter `transpose -t m3` to transpose the music up a minor third:

{% include verovio.html
	source="transpose2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose2">
!!!filter: transpose -t m3
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

The final transposed data (compile filter with <span class="keypress">alt-c</span>):

{% include verovio.html
	source="transpose3"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose3">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[b-e-a-]
=	=
*head:x	*
8eRL	4e-
16eRL	.
16eRJJ	.
8eRL	8gL
8eR	8f
8eR	8e-
8eRJ	8dJ
4eR	4e-
=	=
*-	*-
</script>

If you need to transpose unpitched notes, then temporarily remove the `R` marker, 
and then add it back after transposing the music.  Use the shed filter to
convert `R` into an unused signifier, such as `Z` and then back again after
transposition as an easy method to force unpitched notes to transpose.

{% include verovio.html
	source="transpose4"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="400"
%}
<script type="application/json" id="transpose4">
!!!filter: shed -ke 's/R/Z/g'
!!!filter: transpose -t m3
!!!filter: shed -ke 's/Z/R/g'
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>

The filter `-k -e 's/R/Z/g'` first changes all `R` characters into
`Z` in `**kern` data (`-k` means only process `**kern` spines, and
only data tokens will be processed by default).  Then the `transpose
-t m3` filter transposes all notes up a minor third in both pitched
and previously unpitched notes.  And finally `shed -k -e 's/Z/R/g'`
changes the `Z` characters back into `R` characters.  Here is the
final data after unpitched note transposition:

{% include verovio.html
	source="transpose5"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="transpose5">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[b-e-a-]
=	=
*head:x	*
8gRL	4e-
16gRL	.
16gRJJ	.
8gRL	8gL
8gR	8f
8gR	8e-
8gRJ	8dJ
4gR	4e-
=	=
*-	*-
</script>


## Analysis considerations ##

If you want to do rhythmic analysis with data containing unpitched
notes, nothing special needs to be done to the music.  However, for
pitch analysis with tools that are not aware of the `R` marker,
first convert the `R` into `r` to make these notes appear as rests
in the data.  This can be done easily with the shed filter:

{% include verovio.html
	source="analysis1"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="analysis1">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
</script>


Add the filter `shed -ke 's/R/r/g'` to the data:

{% include verovio.html
	source="analysis2"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="375"
	humdrum-min-width="300"
%}
<script type="application/json" id="analysis2">
!!!filter: shed -ke 's/R/r/g'
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8eRL	4c
16eRL	.
16eRJJ	.
8eRL	8eL
8eR	8d
8eR	8c
8eRJ	8BJ
4eR	4c
=	=
*-	*-
!!!filter: shed -s1 -e 's/[JLKk]//g'
</script>


There is currently a bug in verovio that causes the notation to
not show if there is a beam containing only rests, so the filter
`shed -s1 -e 's/[JLKk]//g'` needs to be added if you want to see
the rests (this is not otherwise necessary preparation for
input to analysis tools, and should be fixed in verovio in the
future).  The `-s1` option means to only apply the sed commands
to the first spine.

And after compiling the filter (with <span class="keypress">alt-c</span>), the
data has rests that were originally unpitched notes:

{% include verovio.html
	source="analysis3"
	pageWidth="1450"
	scale="70"
	humdrum-min-height="345"
%}
<script type="application/json" id="analysis3">
**kern	**kern
*stria1	*
*clefX	*clefG2
*M4/4	*M4/4
*	*k[]
=	=
*head:x	*
8er	4c
16er	.
16er	.
8er	8eL
8er	8d
8er	8c
8er	8BJ
4er	4c
=	=
*-	*-
</script>


## Percussion instrument codes ##

Percussion instruments can be categorized as such with the `*ICidio`
(idiophone) interpretation.  Specific insturments:

| Code  | Name | MIDI key # |
| ----- | ---- | ------ |
| `*Ibdrum`  | bass drum (kit)     | 35    |
| `*Icasts`  | castanets           |       |
| `*Ipiatt`  | cymbals             |       |
| `*Isdrum`  | snare drum (kit)    | 38    |
| `*Icrshc`  | crash cymbal (kit)  | 49/57 |
| `*Igong`   | gong                |       |
| `*Imarac`  | maracas             | 70    |
| `*Iridec`  | ride cymbal (kit)   | 51/59 |
| `*Ispshc`  | splash cymbal (kit) | 55    |
| `*Itabla`  | tabla               |       |
| `*Itambn`  | tambourine          | 54    |
| `*Itom`    | tom-tom drum        | 41/43/45/47/48/50 |
| `*Itrngl`  | triangle            | 81/80 |










