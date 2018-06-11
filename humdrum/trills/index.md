---
title: Trills
lang: en
ref: humdrum-trills
author: Craig Stuart Sapp
translator: 
keywords: humdrum trill
creation_date: 27 Mar 2018
translation_date: 
last_updated: 27 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode trills in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/trills/index.html
---

Trills are encoded in `**kern` spines using either `T` or `t` markers
in note tokens:

{% include verovio.html
	source="trill1"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="application/json" id="trill1">
**kern
2cT
2dT
2et
2fT
2gT
2aT
2bt
*-
</script>

The interval used in the trill is indicated by the case of the letter:
upper-case `T` indicates that the trill interval is a major second, while 
a lower-case `t` indicates a minor second.

When the chromatic alteration of the auxiliary note of the trill 
is not in the key signature or the current state for the given
diatonic pitch, then an accidental for the auxiliary note is given
above the trill mark:

{% include verovio.html
	source="trill2"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="trill2">
**kern
*k[]
2ct
2dt
2eT
2ft
2gt
2at
2bT
*-
</script>

Notice in the above example that any accidental on an auxiliary trill
note will be canceled if a following primary note is on the same
diatonic pitch but with a different chromatic alteration.  For example
the minor second trill on middle C (the first note in the above example)
is to a D-flat. Since the following note is a D-natural, a cancellation
accidental is typically added to the note to avoid performing it as a 
D-flat.  To hide the natural accidentals in the above example, add `ny` 
to the notes to hide the natural signs:

{% include verovio.html
	source="trill3"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="trill3">
**kern
*k[]
2ct
2dnyt
2enyT
2fnyt
2gnyt
2anyt
2bnyT
*-
</script>

The `n` character means that the note has a natural accidental, and the `y`
character means that the natural should not be shown.


## Line extensions ##

Duplicating the trill character in the token will cause an extension line 
to be added to the trill.

{% include verovio.html
	source="trill4"
	humdrum-min-height="220px"
	scale="55"
%}
<script type="application/json" id="trill4">
**kern
*k[]
*M4/4
=1
1cTT
=2
1ett
=3
1gTT
=
*-
</script>


To continue the line extension over several notes, use two trill
characters to start the trill with a line extension, and then use
three trill characters on each note which should be under the same
trill line extension.

{% include verovio.html
	source="trill5"
	humdrum-min-height="330px"
	pageWidth="1000"
	scale="55"
%}
<script type="application/json" id="trill5">
**kern
*k[]
*M4/4
[2ett
=1
2ettt]
4f
[4gTT
=2
1g_TTT
=3
2gTTT
2g#TTT
=5
2a
*-
</script>

Notes under the trill line do not have to all be tied, as demonstrated
by the first G in measure three of the above example.  In addition,
the following G-sharp is included under the trill extension line even though
it is not the same pitch-class as the note that started the trill.

When trills are encoded in the second subspine, the trill marks and 
lines will be placed below the staff automatically:


{% include verovio.html
	source="trill6"
	humdrum-min-height="330px"
	scale="55"
%}
<script type="application/json" id="trill6">
**kern
*k[]
*M4/4
=1
[1cTT
=
2cTTT]
=2
*^
4aT	[1cTT
[4gTT	.
2gTTT_	.
=3	=3
1gTTT]	1cTTT]
*v	*v
=
*-
</script>


