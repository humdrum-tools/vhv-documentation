---
title: White mensural notation
lang: en
ref: humdrum-mens
author: Craig Stuart Sapp
translator: 
keywords: humdrum mensural notation
creation_date: 8 May 2018
translation_date: 
last_updated: 8 May 2018
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode music for white mensural notation.
sidebar: main_sidebar
permalink: /humdrum/mens/index.html
---


White mensural notation can be encoded in Humdrum using the `**mens`
exclusive interpretation.

{% include verovio.html
	source="mens"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="mens">
**mens
*I"Contra
*clefC4
*k[]
*M2/1
*met(C|)
=1-
sp:D
siF
miE
miD
Mp:F
miG
=3-
MiA
MiB-
MiA
sid
mic
miB
sid
=5-
Mir
sic
miB
miA
=6-
Mp:c
mid
sie
=7-
sie
Sie
sp:e
sic
miB
miA
=10-
Mp:B
miA
MiB
Mic
=11-
siA
sid
=12-
*-
</script>

Also see the [kern2mens filter](/filters/kern2mens) to convert `**kern`
data into `**mens` data.

## Pitch ##

`**mens` pitch derives its pitch representation from `**kern`.  The letters a&ndash;g
represent diatonic pitches, with duplicating of letters and change of case controlling
the octave:

{% include verovio.html
	source="octave"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="octave">
**mens
*clefF4
*k[]
*M2/1
*met(C|)
=1-
SFF
SF
Sf
=-
*clefC3
SF
Sf
Sff
=||
*-
</script>


### Accidentals ###

Accidentals are also similar to `**kern` data:

Symbol | Meaning
-------|--------
`-`    | flat sign
`n`    | natural sign
`#`    | sharp sign



{% include verovio.html
	source="accid"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid">
**mens
*clefC3
*k[]
*M2/1
*met(C|)
=-
Sc#
Scn
SB-
SBn
=||
*-
</script>

The treatment of accidentals in `**mens` data is subtly different than in
`**kern` data.  In `**mens` data, accidentals are treated as visual signs by default, 
while in `**kern` data, they are treated as performance accidentals that may or
may not be printed accidentals. 

{% include verovio.html
	source="accid2"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid2">
**mens
*clefC3
*k[]
*M2/1
*met(C|)
=-
Sc#
Sc
Sc#
Sc#
=||
*-
</script>

Compare to an analogous encoding in `**kern` data, where the second note
is also a C-natural, but modern conventions for displaying chromatic
states of notes forces an automatic natural on the note.  And the last
note has a suppressed sharp since the previous notes set the chromatic
state for that diatonic pitch to a sharp.

{% include verovio.html
	source="accid3"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid3">
**kern
*clefC3
*k[]
*M2/1
*met(C|)
=-
0c#
0c
0c#
0c#
=||
*-
</script>

### Editorial accidentals ###

Editorial accidentals are used to clarify the performance accidentals to be
applied to the music.  There are four levels of editorial accidentals, which are
indicated by adding the following characters after an accidental:

Accidental&nbsp;qualifier | Meaning
--------------------------|--------
`y`  | The accidental is strongly implied by the music notation.  This typically means that the accidental is derived from the key signature.  
`yy` | The accidental is weakly implied by the music notation.  This is typically used to indicate the cancellation of a visual accidental.  Roughly equivalent to a cautionary accidental.
`Y`  | A performance accidental.  The accidental is not directly implied by the music notation, but would be inferred by a performer, such as to create a leading tone before a cadence note.
`YY` | A editorial intervention due to a suspected scribal error.  There is a suspected missing visual accidental on the note which is missing.


Here is a typical use of the `y` qualifier to indicate that a B pitch
in the music is flat event hough the note does not have a flat in front
of it since the flat is from the key signature:

{% include verovio.html
	source="accid4"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid4">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
=-
sF
sG
sA
sB-y
sc
sd
se
sf
=||
*-
</script>

Such an accidental can be displayed as an editorial accidental above the note
by placing `*acclev:y` somewhere before the note.  This means that the editorial
accidental level starts at `y` (and also includes `yy`, `Y`, and `YY` levels
as well).  By default, only the `YY` level of accidentals will be displayed
as editorial accidentals.  To also suppress this level of accidental being
displayed as editorial, use `*Xacclev`.

{% include verovio.html
	source="accid5"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid5">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
*acclev:y
=-
sF
sG
sA
sB-y
sc
sd
se
sf
=||
*-
</script>

Mensuration key signatures only affect the pitches of a particular
diatonic pitch, unlike modern keys signatures that apply to the diatonic
pitch class.  An example use of the `yy` qualifier is to caution
that a pitch should be natural when the key signature has a flat in another
octave:

{% include verovio.html
	source="accid6"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid6">
**mens
*clefF4
*k[b-]
*M2/1
*met(C|)
*acclev:yy
=-
sBB-y
sC
sD
sE
sF
sG
sA
sBnyy
=||
*-
</script>

To view this cautionary accidental, either `*acclev:y` or `*acclev:yy` must be used.


The `Y` level for accidentals is used to indicate an unwritten accidental that a
performer would be expected to sing based on performance practice, such as creating
a leading tone before a cadence:

{% include verovio.html
	source="accid7"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="200px"
%}
<script type="application/json" id="accid7">
**mens
*clefC3
*k[b-]
*M2/1
*met(C|)
=-
Sd
sc#Y
Sd
=
*acclev:Y
Sd
sc#Y
Sd
=||
*-
</script>

By default, these accidentals will be hidden in the rendering to graphical notation.
Use `*acclev:Y` to display these accidentals as editorial ones, or use either of the
more generous levels `*acclev:yy` or `*acclev:y` which will also show performance
accidentals as visible editorial ones.


## Rhythm ##

Note rhythms are represented by letters:

<style>

.dense td {
	padding-top: 1px;
	padding-bottom: 1px;
	margin-top: 0;
	margin-bottom: 0;
}

.twocol td:first-child { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(2) { width: 40%; vertical-align: middle}
.twocol td:nth-child(3) { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(4) { width: 40%; vertical-align: middle}

.onecol td:first-child { width: 20%; text-align: center; vertical-align: middle}
.onecol td:nth-child(2) { width: 80%; vertical-align: middle}

</style>


<table class="dense twocol">
<tr><th>Character</th><th> Meaning</th>                             <th>Character</th><th> Meaning</th>  </tr>
<tr><td> X </td><td> maxima (octuple whole note)</td>    <td>   </td>  <td> </td>            </tr>
<tr><td> L </td><td> longa (quadruple whole note)</td>     <td>   </td>  <td> </td>            </tr>
<tr><td> S </td><td> Breve (double whole note)</td>     <td> s </td>  <td> semi-breve (whole note) </td>  </tr>
<tr><td> M </td><td> Minima (half note)</td>     <td> m </td>  <td> semi-minim  (quarter note) </td> </tr>
<tr><td> U </td><td> Fusa (eighth note)</td>       <td> u </td>  <td> semi-fusa (sixteenth note) </td>   </tr>
</table>


{% include verovio.html
	source="rhythms"
	pageWidth="1100"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="280px"
%}
<script type="application/json" id="rhythms">
**mens	**mens
*I"Rests	*I"Notes
*clefC3	*clefC3
Xr	Xc
Lr	Lc
Sr	Sc
sr	sc
Mr	Mc
mr	mc
Ur	Uc
ur	uc
=||	=||
*-	*-
</script>


### Perfection ###

The letter `p` appended to the basic rhythmic value means that the note/rest
is *perfected*.  In modern notation this is equivalent to adding an augmentation
dot after a note, such as a dotted half note.  The letter `i` indicates
an *imperfect* rhythm.  In modern notation all notes are imperfect unless there
is an augmentation dot after it to make it perfect.

The `p` and `i` rhythmic qualifiers are not required unless you are creating
a polyphonic score.  In that case the exact duration of the notes are required
to align the parts.


### Dots ###

Dots representing either augmentation dots or dots of division are encoded
as the character `:`.  This dot does not directly affect the duration of
notes, instead use `p` to perfect notes.  In the future this dot character could
be used to automatically determine if notes are perfect or imperfect,
based on the prevailing mensuration and surrounding notes.

## Mensural signs ##

Mensural signs are indicated by the pattern `*met(X)` where `X` is the
description of the mensuration sign given in the table below.  Common
mensurations are `*met(O)` for circle mensuration, and `*met(C|)` for
Cut-C mensuration.  Here is a table of some of the possible mensurations:


<table class="dense twocol">
<tr><th>Mensuration</th><th> Graphical representation</th>                             <th>Mensuration</th><th> Graphical representation</th>  </tr>

<tr>
	<td> <tt>*met(C|)</tt> </td><td>  <img style="height:20px" src="c-pipe.svg"> </td>    
	<td> <tt>*met(O)</tt>  </td>  <td> <img style="height:20px" src="o.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C)</tt> </td><td>  <img style="height:20px" src="c.svg"> </td>    
	<td> <tt>*met(3)</tt>  </td>  <td> <img style="height:20px" src="n3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C2)</tt> </td><td>  <img style="height:20px" src="c-2.svg"> </td>    
	<td> <tt>*met(O|)</tt>  </td>  <td> <img style="height:20px" src="o-pipe.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|3)</tt> </td><td>  <img style="height:20px" src="c-pipe-3.svg"> </td>    
	<td> <tt>*met(O/3)</tt>  </td>  <td> <img style="height:20px" src="o-over-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(O2)</tt> </td><td>  <img style="height:20px" src="o-2.svg"> </td>    
	<td> <tt>*met(C3)</tt>  </td>  <td> <img style="height:20px" src="c-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C.)</tt> </td><td>  <img style="height:20px" src="c-dot.svg"> </td>    
	<td> <tt>*met(O.)</tt>  </td>  <td> <img style="height:20px" src="o-dot.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(3/2)</tt> </td><td>  <img style="height:20px" src="n3-over-2.svg"> </td>    
	<td> <tt>*met(O3)</tt>  </td>  <td> <img style="height:20px" src="o-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|2)</tt> </td><td>  <img style="height:20px" src="c-pipe-2.svg"> </td>    
	<td> <tt>*met(2)</tt>  </td>  <td> <img style="height:20px" src="n2.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(O|3)</tt> </td><td>  <img style="height:20px" src="o-pipe-3.svg"> </td>    
	<td> <tt>*met(C.|)</tt>  </td>  <td> <img style="height:20px" src="c-dot-pipe.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(Cr)</tt> </td><td>  <img style="height:20px" src="c-reverse.svg"> </td>    
	<td> <tt>*met(C|/3)</tt>  </td>  <td> <img style="height:20px" src="c-pipe-over-3.svg"> </td>
</tr>

<tr>
	<td> <tt>*met(C|/2)</tt> </td><td>  <img style="height:20px" src="c-pipe-over-2.svg"> </td>    
	<td> <tt>*met(C|r)</tt>  </td>  <td> <img style="height:20px" src="c-pipe-reverse.svg"> </td>
</tr>

</table>

Try out the above mensuration signs in this example:

{% include verovio.html
	source="mensuration"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="100"
%}

<script type="application/x-humdrum" id="mensuration">
**mens
*met(C)
Lr
*-
</script>


## Ligatures ##

Ligatures are indicated with angle brackets:

{% include verovio.html
	source="ligature"
	pageWidth="950"
	evenNoteSpacing="1"
	scale="60"
	tabsize="12"
	humdrum-min-height="250px"
%}

<script type="application/x-humdrum" id="ligature">
**mens
*clefC3
*met(C|)
Sic
&lt;sif
sie&gt;
Mid
Mic
siB
Sic
*-
</script>

Currently ligatures can only be shown in *recta* style.


## Barlines ##

Barlines behave the same as in `**kern` data.  Currently barlines are required
in the data in order to break lines of music across multiple systems.  Add a dash
character (`-`) to the barline to make it invisible.


## Coloration ##

To be implemented/described


## Alteration ##

To be implemented/described


