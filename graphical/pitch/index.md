---
title: Pitch
author: Craig Stuart Sapp
creation_date: 7 Mar 2017
last_updated: 7 Mar 2017
tags: [graphical_editing]
sidebar: mydoc_sidebar
keywords: graphical editing pitch
summary: "Description of how to graphically edit the pitch of notes in the VHV notation editor."
permalink: /graphical/pitch/index.html
---

## Stepwise transposition ##

Notes can be transposed to a different line or space on the staff by
clicking on a note and then using the 
<span class="keypress">up</span> and <span class="keypress">down</span>
keys to move the note vertically:

{% include image.html
	file="transpose-note.gif"
	alt="graphically transposing a note"
	max-width="75%"
	caption="Stepwise graphical transposition of a note with <span class='keypress'>down</span>."
%}

Notice that as you move the note with keystrokes in the notation
editor, the corresponding note in the Humdrum data will change
automatically to match the new pitch of the note in the notation.

## Transposing by diatonic interval ##

If you need to transpose a note by more than a step at a time, a faster
transposition method would be to prefix the 
<span class="keypress">up</span> or <span class="keypress">down</span> keystroke
with a digit from <span class="keypress">3</span> through 
<span class="keypress">9</span> to transpose up or down by that diatonic 
interval:

{% include image.html
	file="transpose-thirds.gif"
	alt="graphically transposing a note by thirds"
	max-width="75%"
	caption="Transposing a note up by thirds with <span class='keypress'>3+up</span>."
%}

{% include note.html
	content="In the future, double-clicking on a note in a chord will select all of the notes in the chord, and they will be transposed together. Also, this might also be implemented for entire measures or beamed notes or tuplet groups."
%}

## Transposing by octave ##

The keystrokes
<span class="keypress">shift-up</span>/<span class="keypress">shift-down</span>
can be used as a shortcut to transpose a note by an octave.  This is equivalent
to <span class="keypress">8+up</span>/<span class="keypress">8+down</span>.

{% include image.html
	file="transpose-octave.gif"
	alt="graphically transposing a note by octaves"
	max-width="75%"
	caption="Transposing a note up/down by octave with <span class='keypress'>shift+up</span>/<span class='keypress'>shift+down</span>."
%}


## Accidentals ##

Accidentals can be added to a note by typing


<span class="keypress">minus</span> for flats, 
<span class="keypress">hash</span> for sharps, and
<span class="keypress">n</span> for sharps.  To add double-flats or sharps, 
prefix the accidental keystroke with 
<span class="keypress">2</span>.

{% comment %}
{% include image.html
	file="accidental.gif"
	alt="changing the accidental of a note"
	max-width="75%"
	caption="Changing the accidental of a note."
%}
{% endcomment %}

Repeating the same accidental on a note that already has that accidental
will remove the accidental from the note.


Note that visual accidentals are handled automatically


### Forced display of accidentals ###

Accidentals will not be displayed ... to be continued...











