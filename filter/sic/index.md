---
title: sic filter
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 13 Aug 2020
last_updated:
ref: filters-sic
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/sic/index.html
---

The sic filter is used to control display of simple errors and
corrections for source editions.  Both the original musical content
and the corrected content are encoded in the score, and the sic
filter controls which version is displayed.

Here is an example SIC encoding, where the original notation has a quarter-note
F, but it was determined that a quarter-note G is correct:

{% include verovio.html
	source="sic1"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic1">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>

The lines:

```
!LO:SIC:s=4g
4f
```

mean that the original note in the source edition is a quarter-note
F4, but it has been decided that the correct note should have been
a quarter-note G4.  The `s` parameter means the "substitution"
contents that should replace the following note contents in the
score.




Alternatively, the correction can be displayed, and the SIC parameter can
store what the original notation showed:

{% include verovio.html
	source="sic2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic2">
**kern
*M4/4
=1
4c
4e
!LO:SIC:o=4f
4g
4cc
=
*-
</script>

In this case the `o` parameter means the "original" contents that was replaced
with the correct contents in the score.


## Switching between original and corrected content ##

The sic filter can switch between the original and substitution contents.  To force
the corrections to display, use `!!!filter: sic -s`:

{% include verovio.html
	source="sic3"
	scale="50"
	humdrum-min-width="180"
	humdrum-min-height="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic3">
!!!filter: sic -s
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>

In this example, the score encodes the original contents, but the
sic filter will switch it for the substitution content, so instead
of the `4f` being displayed in the notation, the `4g` is used
instead.

Likewise, if you want to encode the correction in the score, the SIC parameter can
store the original contents, and `!!!filter: sic -o` can be used to show the
original contents that was corrected:


{% include verovio.html
	source="sic4"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sic4">
!!!filter: sic -o
**kern
*M4/4
=1
4c
4e
!LO:SIC:o=4f
4g
4cc
=
*-
</script>

## Displaying sic warnings in VHV ##

If you want to visually mark that notes/rests have SIC layout parameters
attached to them, add the `v` parameter (meaning "verbose"):

{% include verovio.html
	source="sicv"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicv">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g:v
4f
4cc
=
*-
</script>

In the VHV editor, the green "S" is converted into a green triangle icon:



{% include image.html
	file="sic-marker.png"
	alt="sic marker"
	max-width="40%"
	caption="Verbose sic marker dipslay in VHV editor"
%}


Both the original and substitution displays will show a green triangle when 
verbose display is active (it is up to you to know which form is displaying, 
such as by forcing a particular view with the sic filter).


If you want to force display of the sic marker in the graphical 
score, use `!!!filter: sic -v`:


{% include verovio.html
	source="sicv2"
	scale="50"
	humdrum-min-width="180"
	humdrum-min-height="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicv2">
!!!filter: sic -v
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4f
4cc
=
*-
</script>


In the future, another parameter may be added (such as `v=text`) to have
green text show the original/substitution text above the note rather
than a capital S.  So the above example would show `4g` as text instead of `S`.

## SIC for articulations ##


The SIC system is intended for simple corrections to notes/rests.  It can
also be used to indicate obvious problems in articulations:


{% include verovio.html
	source="sicstaccato"
	scale="50"
	humdrum-min-width="180"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sicstaccato">
**kern
*M4/4
=1
4c
4e
!LO:SIC:s=4g
4g'
4cc
=
*-
</script>


In this example, the original score has a staccato on the G, but
this was determined to be an error.  Note that this is different
from implied staccatos, which would be encoded with `y` markers after
the staccatos:


{% include verovio.html
	source="staccato"
	scale="50"
	humdrum-min-width="220"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="staccato">
**kern
*M4/4
=1
4c'
4e'
!LO:TX:b:i:t=simile
4g'y
4cc'y
=
*-
</script>



## SIC for chords ##

The sic filter only replaces entire tokens, so if a single note in
a chord needs fixing, the entire chord will still need to be added
to the SIC `s` or `o` parameter:

{% include verovio.html
	source="chord"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="160"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="chord">
**kern
*M4/4
=1
4c 4e 4g
!LO:SIC:s=4c 4f 4a
4c 4f 4g
=
*-
</script>

Then `!!!filter: sic -s` will produce:

{% include verovio.html
	source="chord2"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="175"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="chord2">
!!!filter: sic -s
**kern
*M4/4
=1
4c 4e 4g
!LO:SIC:s=4c 4f 4a
4c 4f 4g
=
*-
</script>


## SIC for ties ##

Here is an example of using the SIC system for encoding a missing tie.

{% include verovio.html
	source="tie"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="300"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tie">
**kern
*M4/4
=1
4c
4d
4e
!LO:SIC:s=[4f
4f
=2
!LO:SIC:s=4f]
4f
4e
4d
4c
=
*-
</script>

Then `!!!filter: sic -s` will produce:


{% include verovio.html
	source="tie2"
	scale="50"
	humdrum-min-width="220"
	humdrum-min-height="315"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tie2">
!!!filter: sic -s
**kern
*M4/4
=1
4c
4d
4e
!LO:SIC:s=[4f
4f
=2
!LO:SIC:s=4f]
4f
4e
4d
4c
=
*-
</script>



## SIC for slurs ##

Here is an example of using the SIC system for encoding a missing tie.

{% include verovio.html
	source="slur"
	scale="50"
	humdrum-min-width="220"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="slur">
**kern
*M4/4
=1
!LO:SIC:s=(4c
4c
4d
4e
!LO:SIC:s=4f)
4f
=
*-
</script>

Then `!!!filter: sic -s` will produce:

{% include verovio.html
	source="slur2"
	scale="50"
	humdrum-min-width="220"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="slur2">
!!!filter: sic -s
**kern
*M4/4
=1
!LO:SIC:s=(4c
4c
4d
4e
!LO:SIC:s=4f)
4f
=
*-
</script>





