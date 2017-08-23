---
title: Humdrum music encoding tutorial
author: Craig Stuart Sapp
keywords: humdrum ottava marks
creation_date: 20 Aug 2017
last_updated: 20 Aug 2017
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: A tutorial on how to encode music in the Humdrum syntax for VHV.
sidebar: main_sidebar
permalink: /humdrum/getting_started/index.html
---

This tutorial covers the basics of representing graphic music
notation in the Humdrum syntax.  Mostly this involves encoding music
within the `**kern` data representation. For more advanced notational
features, other data types are used, such as `**dynam` for dynamics
and `**text` for lyrics.  Also see other pages in the *Humdrum
encoding* section of the navigation menu for special encoding topics
(to the left or above).

## Pitch ##

Here is a short music example of notes, each containing a rhythm
and then a pitch:

{% include verovio.html
	source="pitch1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="pitch1">
**kern
4c
4d
4e
4f
*-
</script>

`4` represents a quarter note, and `c`, `d`, `e` and `f` represent
the first four pitches of the fourth octave (middle-C octave).  The
musical example is interactive and changes whenever you type
text into the box to the left, so try adding pitches for G, A and B
in the same octave to the notation like this:  

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

Note the order of rhythm and then pitch in the encoded notes.  The
order can be reversed, but the canonical order is rhythm first,
then pitch.  Try reversing the order of a note such as `4c` to `c4`
and see that happens to the note in the graphical notation.

## Clefs ##

VHV will automatically choose the most suitable clef (either bass
or treble) to fit the pitch range of the notes on a staff, but
typically a clef is encoded explicitly for the music.  Clefs are
encoded in *interpretation tokens* that start with a single `*`
followed by the string `clef` and then the shape and line position
of the clef.  For example, a treble clef is `*clefG2`, with `G`
meaning a G-clef, and `2` meaning that the clef is centered on the
second line up from the bottom of the staff.  The bass clef is
`*clefF4` since it is an F-clef on the fourth line of the staff.

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
various repetitions of the pitch name as an upper- or lower-case letter.
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
number can immediately follow the equals sign, representing a measure number.
VHV will display the bar number at each system break, excluding a label for 
measure&nbsp;1:

{% include verovio.html
	humdrum-min-height="525px"
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
=9
1dd
=10
1ee
=11
1ff
=12
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


### Pick-up measures ###

Typically the initial barline should be labeled in the Humdrum encoding 
even though it is not printed.  Either `=1` or `=1-` should be used at the
start of the first measure (with `-` meaning an invisible barline).  Labeling
the first bar is necessary if you need to extract it by measure number with
a tool such as [myank](/filters/myank).

Pickup beats do not have a barline at their start.  If a measure does not
match the duration of the time signature at the start of the music, it will be
automatically interpreted as a pick-up measure and automatically assigned
a measure number of 0 for use with the `myank` filter.

Here is example music with a pick-up beat, and a typical ending which drops
the duration of the pickup measure:

{% include verovio.html
	humdrum-min-height="275px"
	source="bar3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="bar3">
**kern
*clefG2
4G
=1
4c
4c
4c
4e
=2
4g
4e
4e
==
*-
</script>



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

Accidentals must always be indicated along with the diatonic pitch name unless
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

VHV will automatically calculate which accidentals should be visible
in the graphic notation. In the following example, the key signature
contains an F-sharp, so in the first measure no sharps are displayed
on the F's.  The second measure contains an F-natural since there
is no chromatic alteration of the F, so a natural is shown to cancel
out the key signatures F-sharp.  And at the end of the second
measure, the second F has a sharp alteration which must be shown; 
otherwise, it would appear to be an F-natural.

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
visual accidentals, but the accidentals are desired in order to add clarity
for a performer, the accidental of a note can be forced to display by
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

Natural signs do not require `X`, as they are always displayed when
given, but when they are used to indicate a cautionary accidental,
it would be good to include the `X`.

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

The RDF reference record can be placed on any line of the file but
typically is placed at the end of the data.  Notice that editorial accidentals
may affect the visual display of accidentals after the current
pitch.  Try making the natural sign on the last note in the above
example an editorial accidental as well.

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
upper octave in treble clef) cannot be displayed yet.


### Key designation ###

The *key* of the music is different from the *key signature*.
Indicate the key of the music by adding an interpretation in this
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

## Chords ##

Chords are created by adding multiple notes to a token, separated by
a single space character.  Rhythms and articulations of each note should
be duplicated, but not slurs, fermatas or beams.

{% include verovio.html
	source="chord1"
	scale="55"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="chord1">
**kern
*clefG2
4c 4e 4g
4e' 4g' 4cc'
4g^ 4cc^ 4ee^
1c 1e 1g 1cc;
*-
</script>


### Modal key designations ###

The following codes can be appended to the key designation to indicate a 
particular mode:


|  code  | meaning     | example
| ------ | ----------- | ---------
| `dor`  | dorian      | `*d:dor`
| `phr`  | phrygian    | `*e:phr`
| `lyd`  | lydian      | `*F:lyd`
| `mix`  | mixolydian  | `*G:mix`
| `aeo`  | aeolian     | `*a:aeo`
| `ion`  | ionian      | `*C:ion`
| `loc`  | locrian     | `*b:loc`


If the mode is closest to a minor key, then a lower-case letter will be used for the tonic note;
otherwise, modes closer to major use an upper-case for the tonic.


## Rhythm ##

Rhythms in `**kern` data are given in terms of the number of units
the duration of the note will divide a whole note.  Whole notes are `1` since there
is one whole note in a whole note.  Half notes are `2` since there are two in
a whole note.  Quarter notes are `4` since there are four in a whole note, *etc.*

An exception to the numeric system for rhythms is used for some notes
longer than a whole note: breves are represented by `0`, longs are represented
by `00` and maximas by `000`.

{% include verovio.html
	humdrum-min-height="300px"
	evenNoteSpacing="1"
	spacingLinear="1"
	source="rhy1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="rhy1">
**kern
000b
00b
0b
1b
2b
4b
8b
16b
32b
64b
128b
256b
==
*-
</script>

The shortest note value that verovio can display is a 256th note, although shorter values
can be represented in `**kern` data.


### Augmentation dots ###

Augmentation dots are represented by period characters (`.`).  The first one
adds 1/2 the duration of the plain note, 
the next adds an additional 1/4 of the original note, and so on.

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="dots1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dots1">
**kern
4.b
4..b
4...b
4....b
4.....b
=-
4.......b
4........b
4.........b
4..........b
4...........b
==
*-
</script>


## Ties ##

Ties are indicated by attaching `[` to the starting note of a tie,
and `]` on the ending note.  For intermediate notes in a tied group,
the underscore character `_` indicates a previous tie ends on the note
at the same time that a tie starts to the next note.

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="tie1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tie1">
**kern
[4c
=1
4c.]
[8d
=2
2d_
=3
4d] [4a
4a_
=4
2a]
==
*-
</script>


## Beaming ##

Beams work in a similar manner to ties.  The `L` character
indicates the start of a beam, and the `J` character indicates
the end of a beam.

{% include verovio.html
	humdrum-min-height="490px"
	evenNoteSpacing="1"
	source="beam1"
	scale="55"
	pageWidth="475"
%}
<script type="application/x-humdrum" id="beam1">
**kern
*M3/4
=1
8c
8d
8e
8f
8g
8a
=2
8cL
8dJ
8eL
8fJ
8gL
8aJ
=3
*M6/8
8cL
8d
8eJ
8fL
8g
8aJ
==
*-
</script>

Try adding beams with irregular groupings in the first measure of the example.

### Lazy beaming ###

VHV uses a lazy beaming system to beam notes together.  Rather than
specifying the beginning/ending of each sub-beam or beamlet direction,
you instead indicate the beginning/ending of a beamed group of
notes with the `L` and `J` characters (*i.e.*, encode only the primary
sub-beam):

Encoding a full description of sub-beams:

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam2"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam2">
**kern
*M2/4
16.eLL
32fk
16.e
32fJJk
8fL
16gL
16aJJ
==
*-
</script>

which is equivalent to this lazy-beam encoding of only the primary beam (the beam
furthest from the noteheads):

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam3"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam3">
**kern
*M2/4
16.eL
32f
16.e
32fJ
8fL
16g
16aJ
==
*-
</script>

Beams cannot currently be drawn across barlines.  If the beam
beginnings/endings do not balance each other out within a measure, none
of the notes in the measure will be beamed.

{% include verovio.html
	humdrum-min-height="425px"
	evenNoteSpacing="1"
	source="beam4"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam4">
**kern
*M4/4
=1
8cL
8f
8a
8eJ
8fL
8g
8f
8aJ
=2
8cL
8f
8a
8e
8fL
8g
8f
8aJ
==
*-
</script>


### autobeam filtering ###

The [autobeam filter](/filters/autobeam) can be used to beam notes together automatically, 
based on the prevailing time signature:

{% include verovio.html
	humdrum-min-height="365px"
	evenNoteSpacing="1"
	source="beam5"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam5">
**kern
*M3/4
8c
8d
8e
8f
8g
8a
=
*M6/8
8c
8d
8e
8f
8g
8a
==
*-
!!!filter: autobeam
</script>


## Tuplets ##

Tuplets are no different from regular rhythmic values since they
describe how many notes of that duration sum together to create a 
whole-note duration.  Triplet eighth notes are represented with
the number `12` because twelve of them equal a whole-note duration.
quintuplet sixteen notes are represented as `20` since 20 of the
equal a whole-note duration.

{% include verovio.html
	humdrum-min-height="400px"
	evenNoteSpacing="1"
	source="tuplet1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="tuplet1">
**kern
*M2/4
4g
20a
20b
20.a
40g
20a
=
12.f
24g
12a
4g
=
6b
6a
6g
=
2e
==
!!!filter: autobeam
</script>


### Extended Rhythm representation ###

Note durations that do not divide the duration of a whole note into an integer 
number of equal pieces (when also accounting for augmentation dots), must be encoded in an 
extended `**recip` representation.  This system is understood by VHV and
[Humdrum Extras](http://extras.humdrum.org), but not in the classical
Humdrum Toolkit (see [rscale](http://extras.humdrum.org/man/rscale) for
using extended rhythms with the Humdrum Toolkit).

Example extended rhythms include triplet whole notes.  3/2 of a
triplet whole note fill the duration of a regular whole note, so
it is represented by the string `3%2`.  Another way of conceptualizing
this is to flip the numbers in the rhythm string, noting that a triplet
whole note is 2/3rds of a whole note:

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="ext1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="ext1">
**kern
*M2/1
=1
3%2d
3%2e
3%2f
=2
3%2.g
3f
3%2d
=3
1%2e
==
*-
</script>

Notice the `1%2` rhythm in the last measure.  This represent a
double whole note, since 1/2 of the double whole note is equivalent
to a whole note.  `0` is equivalent to `1%2`, `00` is equivalent
to `1%4` (a long) and `000` is equivalent to `1%8` (a maxima).  It
is probably best to use the zero-system for breves, maximas and
longs, reserving extended rhythms for more complicated cases.




## Rests ##

Rests are represent by the character `r` in `**kern` data.
Whole-measure rests are given their actual duration, and if the
duration of the rest matches the time signature, then the rest will
be displayed as a centered whole-measure rest regardless of its actual
duration (or as a breve-measure rest if the duration of the measure
is a breve or longer).

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

Slurs are indicated by adding `(` to a token for the slur start, and `)` for a slur end.

{% include verovio.html
	humdrum-min-height="275px"
	source="slur1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slur1">
**kern
*M4/4
=1
(4c
4d
4e
4f
=2
4g
4f
4e
4c)
==
*-
</script>

### Nested slurs ###

Slurs can be nested by opening another slur while another one is active. 
The first slur closing will affect the closest slur opening to it.

{% include verovio.html
	humdrum-min-height="300px"
	source="slur2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slur2">
**kern
*M4/4
=1
(4c
(>4d
(4e
(>4f
=2
4g)
4f)
4e)
4c)
==
*-
!!!RDF**kern: > = above
</script>

Notice the direction RDF character which can be used to force
the direction of a slur.

## Articulations and ornaments ##

Here is a sampler of note articulations:

{% include verovio.html
	humdrum-min-height="250px"
	source="artic1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic1">
**kern
4ff'
4ff^
4ff`
4ff~
4ff'~
4ff'^
4ff^^
4ff;
=
*-
</script>

Articulations can be place on the opposite side of their automatic location
by adding RDF entries to force the articulation above or below the notehead:

{% include verovio.html
	humdrum-min-height="275px"
	source="artic2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic2">
**kern
4f'>
4ff^<
4f`>
4ff~<
4f'~>
4ff'^<
4f^^>
4ff;<
=
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


Here is a sampler of ornaments.  Upper-case ornaments indicate
whole-tone auxiliary notes, and lower-case ornaments indicate
semi-tone auxiliary notes.  If the auxiliary notes require accidentals
in the graphical music notation, then will be added automatically, as
well as cautionary accidentals that may be needed on primary notes
which follow the auxiliary notes of the ornaments.

{% include verovio.html
	humdrum-min-height="250px"
	source="orn1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="orn1">
**kern
*M4/4
=1
2ct
2dT
=2
2fW
2gw
=
2fm
2gM
==
*-
</script>


## Lyrics ##


Lyrics are added to a staff by placing one or more `**text` spines after a `**kern` spine.

{% include verovio.html
	humdrum-min-height="250px"
	source="text1"
	scale="55"
	pageWidth="1200"
%}
<script type="application/x-humdrum" id="text1">
!!!OTL@@DE: Liebes-A-B-C
!!!COM: Pohlenz, August
!!!CDT: 1790/07/03/-1843/03/09/
!!!ODT: 1827
!!!OMD: Allegretto
!!!LYR: Gerhard, Wilhelm
!!!LDT: 1826
!!!OCL: Erk, Ludwig
!!!GCO: Deutscher Liederschatz, Band 1
**kern	**text	**text	**text	**text	**text	**text	**text
*clefG2	*	*	*	*	*	*	*
*k[b-]	*	*	*	*	*	*	*
*F:	*	*	*	*	*	*	*
*M3/8	*	*	*	*	*	*	*
=1	=1	=1	=1	=1	=1	=1	=1
8f	A	E	I	M	Q	U	Yp-
8e	B	F	K	N	R	V	-si-
8f	C	G	und	O	S	W	-lon
=2	=2	=2	=2	=2	=2	=2	=2
4g	D,	H,	L,	P,	T,	X,	Z,
8r	.	.	.	.	.	.	.
=3	=3	=3	=3	=3	=3	=3	=3
8g	wenn	w&auml;rst	Aeug-	gleich	Schei-	mach'	nun
8f	ich	du	-lein	ei-	-den	ei-	geh'
8g	dich	doch	so	-ner	thut	-nen	zu
=4	=4	=4	=4	=4	=4	=4	=4
4a	seh',	da!	hell	Fee	weh.	Knix,	Bett!
8r	.	.	.	.	.	.	.
=5	=5	=5	=5	=5	=5	=5	=5
8a	dich,	Dr&uuml;ck-	gl&auml;nz-	fes-	Hal-	dr&uuml;ckt	Bricht
8a	mei-	-te	-ten	-selst	-te	dir	doch
8dd	-ne	mein	in	du	mit	ein	die
=6	=6	=6	=6	=6	=6	=6	=6
8.cc	s&uuml;-	treu-	Lie-	Herz	Herz	jun-	Nacht
16b-	-sse	-er	-bes-	und	und	-ger	schon
8b-	Lust,	Arm,	-pracht	Sinn,	Mund	Fant	ein,
=7	=7	=7	=7	=7	=7	=7	=7
8g	klopft	Hol-	mir	Gr&uuml;b-	treu	z&auml;rt-	kann
8g	die	-de,	aus	-chen	an	-lich	ja
8cc	em-	dich	der	in	dem	die	nicht
=8	=8	=8	=8	=8	=8	=8	=8
8.b-	-p&ouml;r-	lie-	Wim-	Wang'	Lie-	Schwa-	bei
16a	-te	-be-	-pern	und	-bes-	-nen-	dir
8a	Brust,	warm!	Nacht,	Kinn,	-bund,	-hand,	sein,
=9	=9	=9	=9	=9	=9	=9	=9
8f	wird	Sch&auml;tz-	tra-	Ro-	sa-	a-	wenn
8e	mir	-chen,	-fen	-sen-	-ge	-ber	ich
8f	so	ach	wie	-glut,	mir	nur	auch
=10	=10	=10	=10	=10	=10	=10	=10
8.ee	wohl	w&auml;rst	bli-	Li-	nie	ern-	Fl&uuml;-
16dd	und	du	-tzes-	-lien-	A-	-sten	-gel
8dd	weh,	da!	-schnell,	schnee,	de!	Blicks	h&auml;tt'!
=11	=11	=11	=11	=11	=11	=11	=11
8cc	wenn	w&auml;rst	Aeug-	rei-	Schei-	mach'	Geh'
8g	ich	du	-lein	-zen-	-den	ihm	nur
8a	dich	mir	so	-de	thut	den	zu
=12	=12	=12	=12	=12	=12	=12	=12
4f	seh'!	nah'!	hell.	Fee!	weh.	Knix!	Bett!
8r	.	.	.	.	.	.	.
==	==	==	==	==	==	==	==
*-	*-	*-	*-	*-	*-	*-	*-
!!!SMS: Deutscher Liederschatz, Band 1, Ludwig Erk, ed.
</script>


## Dynamics ##

Dynamics are added to the staff as a separate spine to the right of a `**kern`
spine to which the dynamics should be associated with.

{% include verovio.html
	humdrum-min-height="350px"
	source="dynam1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="dynam1">
**kern	**dynam
*clefG2	*
*M4/4	*
=1	=1
4c	p
4d	<
4e	(
4f	(
.	[
=2	=2
2g	f
.	>
4f	)
4d	)
=	=
1c	]
==	==
*-	*-
</script>

When lyrics are present, dynamics will automatically be placed above the staff:

{% include verovio.html
	humdrum-min-height="350px"
	source="dynam2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="dynam2">
**kern	**dynam	**text
*clefG2	*	*
*M4/4	*	*
=1	=1	=1
4c	p	The
4d	<	ru-
4e	(	-ler
4f	(	of
.	[	.
=2	=2	=2
2g	f	the
.	>	.
4f	)	realm
4d	)	was
=	=	=
1c	]	seen
==	==	==
*-	*-	*-
</script>


Note that the order of the `**dynam` and `**text` spines does not matter.


## Multiple voices on a staff ##

Spine split manipulators (`*^`) and spine merge manipulators (`*v`) are used
to add or remove voices/layers on a staff.  Note that the highest part 
on the staff will typically be left most (opposite of the staff ordering 
from lowest to highest).

{% include verovio.html
	humdrum-min-height="210px"
	source="multi1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi1">
**kern
*M4/4
*^
2..gg	4b
.	4a
.	4g
.	4f
8ff	.
*v	*v
=
*-
</script>

Notes sounding together in the different voices are placed on the same line, and
if the other voice is sustaining, a `.` character is used as a place holder for
that voice (the dot is called a *null token* in Humdrum terminology).

### Partial voices/layers ###

Voices/layers which do not continue throughout the measure can be encoded
in two equivalent manners: (1) splitting and merging the spine as needed in 
the measure, or (2) adding invisible rests to fill in the voice/layer for the
entire measure.  For method #1, note that the spine merging cannot occur until 
the end of both sounding notes in each layer.

{% include verovio.html
	humdrum-min-height="360px"
	source="multi2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi2">
**kern
*M4/4
=1
*^
2cc	4a
.	4g
*v	*v
4f
4e
=2
*^
2cc	4a
.	4g
2ryy	4f
.	4e
*v	*v
=
*-
</script>



## Multiple staves ##

Each `**kern` spine in the data will produce a staff in the graphical notation.
The lowest staff is the left-most spine in the data, and the highest staff
in the notation is the right-most spine.


{% include verovio.html
	humdrum-min-height="360px"
	source="staves1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="staves1">
**kern	**kern
*M4/4	*M4/4
=1	=1
*	*^
1E	2cc	4a
.	.	4g
*	*v	*v
.	4f
.	4e
=2	=2
*	*^
1E	2cc	4a
.	.	4g
.	2ryy	4f
.	.	4e
*	*v	*v
=	=
*-	*-
</script>


## Cross-staff notes ##

Notes can be stored in one `**kern` spines, but appear in another staff by
applying an orientation RDF marker immediately after a note's pitch.

{% include verovio.html
	humdrum-min-height="360px"
	source="cross1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="cross1">
**kern	**kern
*clefF4	*clefG2
*M4/4	*M4/4
=1	=1
1CC	16e
.	16d
.	16c
.	16B<
.	16G<
.	16F<
.	16E<
.	16D<
.	16C<
.	16BB<
.	16C<
.	16E<
.	16G<
.	16c<
.	16e
.	16g
=2	=2
16C	2cc/
16D	.
16E	.
16F	.
16G	.
16A	.
16B	.
16c>	.
16d>	2dd/
16e>	.
16f>	.
16g>	.
4f>\	.
=	=
*-	*-
!!!filter: autobeam
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


## Text directions ##

Text can be displayed in the graphical notation by adding a text 
layout direction to the encoding:


{% include verovio.html
	humdrum-min-height="360px"
	source="dir1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dir1">
**kern
*clefG2
*M4/4
=1
!LO:TX:b:i:t=cresc.
4c
2d
4f
=2
!LO:TX:a:i:t=accel.
4f
!LO:TX:b:t=comment&colon; 42
4d
4e
4c
==
*-
</script>

Text layout comments start with `!LO:TX:` and are placed immediately before the note
to which they are attached.  The parameter `a` means place the text above, and `b` means
place the text below. The font is roman by default; adding an `i`  parameter will 
make the text italic, and `b` to make it bold.  The actual text is given by the
`t` parameter, such as "*cresc.*" with the parameter `t=cresc.`.  Note that parameters
are separated by colons, and &amp;colon; is used to insert a colon into the text string.


