---
title: Humdrum music encoding tutorial
author: Craig Stuart Sapp
keywords: humdrum ottava marks
creation_date: 20 Aug 2017
last_updated: 20 Aug 2017
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: A tutorial on how to encode music in the Humdrum syntax.
sidebar: main_sidebar
permalink: /humdrum/getting_started/index.html
---

Here is a tutorial about representation graphical music notation
in the Humdrum syntax.  Mostly this involves encoding music within
the `**kern` data representation. For more advanced notational
features, other data types are used, such as `**dynam` for dynamics
and `**text` for lyrics.

## Pitch ##

Here is a short music example of notes, each containing a rhythm
and then a pitch:

{% include verovio.html
	source="pitch1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch1">**kern
4c
4d
4e
4f
*-
</script>

`4` represents a quarter note, and `c`, `d`, `e`, and `f` represent
the first four pitches of the fourth octave (middle-C octave).  
The musical example is interactive and changes whenever you type
text into the box on the left, so try adding pitches for G, A and B
in the same octave:  

{% include verovio.html
	humdrum-visible="false"
	source="pitch2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch2">
**kern
4c
4d
4e
4f
4g
4a
4b
*-
</script>


Experiment with the numbers to generate other
rhythms, such as half notes and eighth notes:

{% include verovio.html
	humdrum-visible="false"
	source="pitch3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch3">
**kern
8c
2d
8e
8f
4g
4a
2b
*-
</script>

Note the order of rhythm and then pitch in the encoded notes.  You
can reverse the order and place pitch first, but the canonical
order is rhythm, then pitch.  Try reversing the order of a note
such as `4c` to `c4` and see that happens to the note in the graphical
notation.

## Clefs ##

VHV will automatically choose the most suitable clef (either bass
or treble) to fit the pitch range of the music, but typically a
clef is encoded explicitly in the music.  Clefs are encoded in
*interpretation tokens* which start with a single `*` followed by
the string `clef` and then the shape and line position of the clef.

For example, a treble clef is `*clefG2`, with `G` meaning a G-clef,
and `2` meaning that the clef is centered on the second line up
from the bottom of the staff.  The bass clef is `*clefF4` since it
is an F-clef on the fourth line of the staff.

{% include verovio.html
	source="clef1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="clef1">
**kern
*clefG2
1c
*clefF4
1c
*clefC3
1c
*-
</script>

Try moving the clefs to different stafflines by changing the number 
after the clef shape.

The vocal tenor clef is represented by `*clefGv2`, where the `v`
means the music should be played an octave lower than the regular
treble clef.  Try creating a vocal tenor clef in the above interactive
example. The `v` operator also works on the other clefs (but these
sorts of clefs are very rare).  Another rare clef is `*clefG^2`
which is the opposite of `*clefGv2`, where the music is written
an octave lower than actually sounding pitch for the normal form 
of the clef.

## Octaves ##

The octave position of a note is indicated in `**kern` data as
various repetitions of the pitch as an upper- or lower-case letter.
The middle-C octave is indicated by single lower case letters, and each
successively higher octave repeats an additional lower-case letter to indicate
the octave:

{% include verovio.html
	source="octave1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="octave1">
**kern
*clefG2
2c
2cc
2ccc
*-
</script>

Lower octaves are indicated by successive repetitions of upper-case letters:

{% include verovio.html
	source="octave2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="octave2">
**kern
*clefF4
2C
2CC
2CCC
*-
</script>


## Barlines ##

Barlines are indicated by a *token* starting with an equals sign.  A optional 
number can immediately follow the equals sign, which represents a measure number.
VHV will display the bar number at each system break, excluding a label for 
measure&nbsp;1:

{% include verovio.html
	source="bar1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="bar1">
**kern
*clefG2
=1
1c
=2
1d
=3
1e
=4
1f
=5
1g
=6
1a
=7
1b
=8
1cc
=8
1dd
=8
1ee
=8
1ff
=8
1gg
=
*-
</script>


Following the measure number can be an optional styling for the barline. `-` means an
invisible barline, `||` is a double thin barline, `|!:` is a left-repeat, 
`:|!|:` is a left-right repeat.  A special style is `==`, representing a final
barline.  This bar usually does not include a bar number, since it is the last
one in the piece/movement.

{% include verovio.html
	source="bar2"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="bar2">
**kern
*clefG2
=1
1c
=2-
1d
=3||
1e
=4!!
1f
=5!|:
1g
=6:|!|:
1a
=7:|!
1b
==
*-
</script>


Humdrum can represent more barline styles, but the above types are currently
supported in verovio.

## Time signatures ##

Time signatures are interpretations in the form `*MX/Y` where `X` is the top
number of the signature and `Y` is the bottom number of the signature:

{% include verovio.html
	humdrum-min-height="310px"
	source="time1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="time1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M3/2
2g
2f
2d
=
*-
</script>



### Meter symbols ###

Cut-time and Common-time symbols can be displayed by including an interpretation
in the form `*met(X)`, where `X` is `c|` for cut-time, or `c` for common time:

{% include verovio.html
	humdrum-min-height="310px"
	source="meter1"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="meter1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M2/2
*met(c|)
2g
2a
=
*-
</script>



## Accidentals ##

Accidentals must always be indicated along with the diatonic pitch name, unless
the pitch is natural.  Accidentals up to double-sharp/flat can be displayed in
VHV (no triple sharps/flats or higher can be rendered with verovio, although 
they can be represented in `**kern` data):


{% include verovio.html
	source="acc1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc1">
**kern
*clefG2
4c--
4d-
4en
4f#
4g##
*-
</script>

VHV will automatically calculate which accidentals should be visible. In
the following example, the key signature contains an F-sharp,
so in the first measure, no sharps are displayed on the F's.  The
second measure contains an F-natural since there is no chromatic
alteration of the F, so a natural is shown to cancel out the key
signatures F-sharp.  And at the end of the second measure, the
second F has a sharp alteration which must be showing in this case,
otherwise it would appear to be an F-natural.

{% include verovio.html
	humdrum-min-height="300px"
	source="acc2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc2">
**kern
*clefG2
*k[f#]
=1
4g
4f#
4e
4f#
=
4g
4f
4e
4f#
==
*-
</script>

Try removing the key signature, and see what happens to the accidentals displayed
in the example.

### Cautionary accidentals ###

When accidentals are not required according to the algorithm for calculating
visual accidentals, but the accidentals are desired in order to avoid confusion
for the performer, the accidental of the note can be forced to display by
adding `X` after the accidental.


{% include verovio.html
	humdrum-min-height="300px"
	source="acc3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc3">
**kern
*k[f#]
*clefG2
=1
4g
4f
4e
4f
=
4g
4f#X
4e
4f#
==
*-
</script>

In the first measure, two F-naturals are given, with only the first
F-natural displaying its natural alteration.  In the second measure,
the first F has a sharp, but this sharp would not normally be
displayed since it is within the key signature, and the barline
canceled out the F-natural of the previous measure.  To avoid
confusion, the first F-sharp in the second measure should have a
cautionary sharp added to the note as is shown in the above example.

Natural signs do not require `X`, but when they are used to indicate
a cautionary accidental, it would be good to include the `X`.

### Editorial accidentals ###

Editorial accidentals can be indicated by adding an RDF reference record
for a user-signifier (character) used to mark the editorial accidentals
in the data.  Typically the character `i` is used to mark editorial
accidentals in [Josquin Research Project](http://josquin.stanford.edu) 
Humdrum encodings:

{% include verovio.html
	humdrum-min-height="210px"
	humdrum-min-width="400px"
	source="acc4"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc4">
**kern
*clefG2
=1
4g
4f#i
4e
4f
==
*-
!!!RDF**kern: i = editorial accidental
</script>

The RDF reference record can be placed on any line of the file, but
typically is placed after the data.  Notice that editorial accidentals
may affect the visual display of accidentals after the current
pitch.  Try making the natural sign on the last note an editorial
accidental as well.

Also note that the style of the editorial accidental can be controlled
from the RDF entry.  Add the string `brack` or `bracket` to the RDF description
so that the editorial accidentals are displayed as regular accidentals enclosed
in brackets.  Also try adding `paren` or `parentheses` to the RDF line to 
display the editorial accidental in parentheses.

## Key signatures ##

Key signatures are represented by interpretations in the form `*k[X]`, where `X`
is a list of the accidentals in the order in which they are displayed in the
key signature.  Here a scale in C-sharp major and C-flat major, showing all of the
accidentals in their proper order:

{% include verovio.html
	humdrum-min-height="475px"
	source="key1"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="key1">
**kern
*k[f#c#g#d#a#e#b#]
*clefG2
=1
4c#
4d#
4e#
4f#
4g#
4a#
4b#
4cc#
=2
*k[b-e-a-d-g-c-f-]
4c-
4d-
4e-
4f-
4g-
4a-
4b-
4cc-
==
*-
</script>


Verovio cannot handle changing the order of the flats, and key
signatures such as `*k[F#4F#5]` (showing F-sharps on the lower and
upper octave in treble clef) cannot be displayed properly in graphical
notation.


### Key designation ###

The *key* of the music is different from the *key signature*.
Indicate the key of the musing by adding an interpretation in this
form `*X:`, where `X` is a pitch name plus possible accidental,
with lower-case pitch names indicating minor keys, and upper-case
pitch names indicating major keys.  For example, `*C:` means C
major, and `*a:` means A minor (note that both have the key signature
`*k[]` where there are no sharps or flats).

The key designation typical follows the key signature, or can appear
on its own if the key changes but the key signature does not.

{% include verovio.html
	humdrum-min-height="450px"
	source="key2"
	scale="55"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="key2">
**kern
*clefG2
*k[f#]
*G:
=1
4g
4dd
4b
4g
=2
*e:
4e
4b
4g
4e
=3
*c#:
4c#
4g#
4e
4c#
==
*-
</script>

Note that the music in the last measure does not have a key signature change
even though the music modulates to C-sharp minor.



## Rhythm ##


### Augmentation dots ###

### Ties ###

## Rests ##

Rests are represent by the character `r` in `**kern` data.  Whole
measure rests are given their actual duration, and if the duration
of the rest matches the time signature, then the rest will be
displayed as a whole-measure rest regardless of its actual duration
(or as a breve-measure rest if the duration of the measure is a breve
or longer).

{% include verovio.html
	humdrum-min-height="275px"
	source="rest1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="rest1">
**kern
*clefG2
*M5/4
=1
4r
2.r
32r
8r
16r
32r
=2
4%5r
==
*-
</script>


## Slurs ##

## Chords ##

## Beaming ##

## Articulations and ornaments ##

## Dynamics ##

## Lyrics ##

## Multiple voices on a staff ##

## Multiple staves ##

## Cross-staff notes ##



