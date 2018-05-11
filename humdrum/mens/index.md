---
title: White mensural notation
author: Craig Stuart Sapp
keywords: humdrum mensural notation
creation_date: 8 May 2018
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

Also see the [kern2mens filter](/filters/kern2mens) to conver `**kern`
data into `**mens` data.

## Pitch ##

`**mens` pitch adopts the pitch representation of `**kern` data.

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
is *perfected*.  In modern notation this is equivalent to adding an augmentatin
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


