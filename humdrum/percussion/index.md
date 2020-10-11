---
title: Percussion
lang: en
ref: humdrum-tuplet_styling
author: Craig Stuart Sapp
translator: 
keywords: humdrum percussion
creation_date: 11 Oct 2020
translation_date: 
last_updated: 11 Oct 2020
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Encoding methods for percussion parts.
sidebar: main_sidebar
permalink: /humdrum/percussion/index.html
---

Percussion parts are encoded in `**kern` spines, using a percussion
clef and markers to indicate unpitched or semipitched notes, as
well as interpretation or layout parameter control of notehead shapes.

## Percussion clef ##

Use `*clefX` for a percussion clef, with `X` meaning unpitched.

{% include verovio.html
	source="xclef"
	pageWidth="1450"
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

Percussion notes should include `R` to indicate that they are
unpitched.  This is important for analysis purpose, so percussion-clef
notes without an `R` qualification will be highlighted in red.

{% include verovio.html
	source="unpitched"
	pageWidth="1450"
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

If notes are not pitched, but also not fully unpitched, the marker `RR` can be used
to indicate that a note is partially pitched.  This is useful for instruments such
as the tom-tom where the drums are pitched from low to high.


{% include verovio.html
	source="semipitched"
	pageWidth="1450"
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

Notehead shapes can be set either by layout parameters applied to the note,
or a notehead shape interpretation.   Available notehead shapes:

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




