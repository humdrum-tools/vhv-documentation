---
title: Pitch
author: Craig Stuart Sapp
creation_date: 7 Mar 2017
last_updated: 7 Mar 2017
tags: [all, graphic_editing, RDF]
sidebar: main_sidebar
keywords: graphic editing pitch
datatable: true
vim: ft=javascript
summary: "Graphically altering note pitches and accidentals in the notation editor."
permalink: /graphic/pitch/index.html
---

## Key command summary ##
{% include keytable.html
	contentId="slurkeysummary"
%}
<script type="text/JSON" id="slurkeysummary">
{
	"tableColumns":
	[
		{ "data": "keys",   "title": "Key(s)" },
		{ "data": "description", "title": "Action"}
	],
	"categoryList": 
	[

		{
			"categoryName": "diatonic pitch",
			"keyList":
			[
				{
					"keys": "<span class='keypress'>up</span>",
					"description": "transpose up a step"
				},
				{
					"keys": "<span class='keypress'>down</span>",
					"description": "transpose down a step"
				},
				{
					"keys": "<span class='keypress'>shift-up</span>",
					"description": "transpose up an octave"
				},
				{
					"keys": "<span class='keypress'>shift-down</span>",
					"description": "transpose down an octave"
				},
				{
					"keys": "<span class='keypress'>3+up</span>",
					"description": "transpose up a third"
				},
				{
					"keys": "<span class='keypress'>5+down</span>",
					"description": "transpose down a fifth"
				}
			]	
		},

		{
			"categoryName": "accidentals",
			"keyList":
			[
				{
					"keys": "<span class='keypress'>hash</span>",
					"description": "toggle sharp accidental"
				},
				{
					"keys": "<span class='keypress'>minus</span>",
					"description": "toggle flat accidental"
				},
				{
					"keys": "<span class='keypress'>n</span>",
					"description": "toggle forced natural accidental"
				},
				{
					"keys": "<span class='keypress'>2+hash</span>",
					"description": "toggle double-sharp accidental"
				},
				{
					"keys": "<span class='keypress'>2+minus</span>",
					"description": "toggle double-flat accidental"
				}
			]	
		},

		{
			"categoryName": "accidental manipulation",
			"keyList":
			[
				{
					"keys": "<span class='keypress'>x</span>",
					"description": "toggle forced display of accidental"
				},
				{
					"keys": "<span class='keypress'>i</span>",
					"description": "toggle editorial accidental"
				}
			]	
		}
	]
}
</script>


## Stepwise transposition ##

Notes can be transposed to a different staffline or space by
clicking on a note and then using the
<span class="keypress">up</span> and <span class="keypress">down</span>
arrow keys to move it vertically.  Below is a demonstration
where the D5 pitch is moved down by step to D4:

{% include image.html
	file="transpose-note.gif"
	alt="graphically transposing a note"
	max-width="75%"
	caption="Stepwise graphic transposition of a note with <span class='keypress'>down</span>."
%}

Notice that as the note moves down in the notation
editor, the corresponding note in the Humdrum data will change
automatically to match the new pitch of the note in the notation.

## Transposing by diatonic interval ##

If you need to transpose a note by more than a step at a time, a faster
transposition method prefixes the
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

Accidentals can be added to a selected note by pressing
<span class="keypress">minus</span> for a flat,
<span class="keypress">hash</span> for a sharp, and
<span class="keypress">n</span> for a natural.  To add a double-flat or double-sharp,
prefix the accidental keystroke with the digit
<span class="keypress">2</span>.

Repeating the same accidental on a note that already has that
accidental will remove the accidental from the note.  An easy way
to remove any accidental other than a natural sign would be to type
<span class="keypress">n+n</span>: once to convert the accidental
into a natural sign, and another to remove the natural sign (the
note will still possess an implicit natural, however).

{% include image.html
	file="accidentals.gif"
	alt="changing the accidental of a note"
	caption="Graphically adding/removing accidentals."
%}


{% comment %}
Cross-staff visual accidentals
{% endcomment %}



## Printed vs. sounding accidentals ##

Humdrum `**kern` pitches always encode *sounding* accidentals.  VHV automatically
calculates visual accidentals when converting to [MEI](http://www.music-encoding.org)
for rendering to graphic music notation.


However there can be exceptions to the visual accidental calculation
rules, which are demonstrated in the sub-sections below.

1. *forced accidentals*: the accidental can be forced to display on a selected note by pressing <span class="keypress">x</span>.
1. *suppressed accidentals*: don't show the accidental regardless of whether or not it should be shown. (not currently available in graphic editing).

Below is a demonstration of changing accidentals in the music. Notice that
altering the accidental on one a note may automatically add a different visual
accidental on a following note in the measure.

{% include image.html
	file="visual-accidentals.gif"
	alt="automatic calculations of printed accidentals"
	caption="Demonstration of printed accidental calculations."
%}


As demonstrated in the above figure, if a grace note has a printed
accidental, the next note on the same staff line or space in the
measure will be given a forced accidental.  If you don't want this
automatic courtesy accidental add a `y` after the accidental in the
Humdrum data.


### Forced accidentals ###

Accidentals can be forced to display in the notation by typing the
key <span class="keypress">x</span> while editing a note (mnemonic:
e**X**plicit).  This will add the character `X` (capital x) after
the accidental for the note data, which means to explicitly show
the accidental in the notation.  Forced accidentals are typically
used to remind a performer that the note has the given accidental,
such as when an accidental is canceled by a barline and a note in
the following measure is spelled according to the key signature
again.  Forced accidentals used for this purpose are called courtesy
or cautionary accidentals.

{% include image.html
	file="forced-accidentals.gif"
	alt="forcing the display of accidentals"
	max-width="100%"
	caption="Forcing the display of accidentals with <span class='keypress'>x</span>."
%}

Natural signs (`n`) in `**kern` data are automatically treated as
forced accidentals when converting Humdrum data into notation.  To
create a forced natural, you should instead type <span
class="keypress">n</span> to add a natural sign.

{% include note.html
	content="Some things need to be cleaned up in the graphic editing implementation of forced accidentals: (1) typing <span class='keypress'>x</span> should toggle the forced accidental signifier, (2) typing <span class='keypress'>x</span> on a note with an implicit natural should insert an `n` for an explicit natural rather than `nX` which is a doubly explicit natural sign, and (3) `X` should be removed when deleting an accidental from the note (converting the accidental into an implicit natural)."
%}

### Suppressed accidentals ###

VHV will automatically suppress printed accidentals on notes that otherwise
require them if they are tied over from previous measures:

{% include image.html
	file="accidental-suppressed-tie.png"
	alt="graphically transposing a note"
	max-width="75%"
	caption="Visual accidentals are automatically suppressed for notes tied over barlines."
%}

Explicitly suppressing visual accidentals cannot be done within the notation editor
(yet), but this can be accomplished by adding a single `y` after the
accidental in the text editor.

### Ornament accidentals ###

Ornaments containing auxiliary accidentals will automatically force an accidental
on a following note if it is different from that of the auxiliary accidental.

{% include image.html
	file="ornament-accidentals.gif"
	alt="Ornamental accidentals"
	caption="Automatically forced accidentals after ornaments.  (typing <span class='keypress'>m</span>, <span class='keypress'>w</span>, and <span class='keypress'>T</span>)"
%}


## Editorial accidentals ##

The VHV notation editor allows toggling of accidentals between regular and
*editorial* forms. Press <span class="keypress">i</span> to switch between
these two types of accidentals.

{% include image.html
	file="editorial-accidentals.gif"
	alt="editorial accidentals"
	max-width="90%"
	caption="Creating, removing and changing editorial accidentals."
%}

To indicate an editorial accidental, an RDF signifier has to be
added to the data:


```
!!!RDF**kern: i = editorial accidental
```

Any user-signifier other than `i` can also be used.  If no editorial
accidental RDF is found in the data, one will be inserted at the
bottom of the Humdrum content automatically; otherwise, the signifier
for an existing editorial accidental RDF entry will be used (even
if it is not&nbsp;`i`).

Editorial accidentals will always be forced to display, so adding
a forced display signifier (`X`) with the <span class="keypress">x</span>
key is not necessary.

{% include note.html
	content="Perhaps editorial accidentals should be allowed to be suppressed, as they currently cannot."
%}

{% include warning.html
	content="Automatic insertion of an editorial accidental RDF is currently hardwired to the \"i\" user-signifier, so you should not use the same signifier in the file for a different meaning in kern data unless you manually add an editorial accidental RDF using a different user-signifier."
%}

{% include note.html
	content="A small accidental above a note is the common style for editorial accidentals in editions of Renaissance music (typically to indicate an unwritten *musica ficta* accidental).  Other rendering styles for editorial accidentals are not (yet) available."
%}




