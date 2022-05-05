---
title: Harmonics
lang: en
ref: humdrum-harmonics
author: Craig Stuart Sapp
translator: 
keywords: humdrum harmonics
creation_date: 29 Apr 2019
translation_date: 
last_updated: 29 Apr 2019
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode harmonics in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/harmonics/index.html
---

# Natural harmonics #

Natural harmonics are encoded at their sounding pitch and a small
letter `o` is added to the note to indicate that it is a 
natural harmonic:

{% include verovio.html
	source="natharm"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="natharm">
**kern
*Ivioln
*clefG2
*M4/4
=1
4go
4ddo
4aao
4eeeo
=
*-
</script>

# Fingered harmonics #

Fingered harmonics consist of three components: a stopped note, a
lightly-touched note on a node of the harmonic, and the sounding
pitch.  The stopped and touched notes do not make a sound, so
they are encoded as rests, while the sounding note is encoded as a
regular note.

When encoded as rests, the stopped and touched note rests are 
given a pitch as demonstrated in the following example for the
third harmonic on violins:

{% include verovio.html
	source="fingharm"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fingharm">
**kern
*Ivioln
*clefG2
=1
2rA 2re 2ee
4rd 4ra 4aa
4ra 4re 4ee
2ree 2rbb 2bbb
=
*-
</script>

Note that the lightly touched note is automatically displayed
as a diamond-shaped note.

The sounding note can be hidden by adding `yy` to the sounding note:

{% include verovio.html
	source="fingharmnosound"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fingharmnosound">
**kern
*Ivioln
*clefG2
=1
2rA 2re 2eeyy
4rd 4ra 4aayy
4ra 4ree 4eeeyy
2ree 2rbb 2bbbyy
=
*-
</script>

Or the sounding note can be displayed while the non-sounding notes
hidden in a similar manner:

{% include verovio.html
	source="fingharmnorest"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fingharmnorest">
**kern
*Ivioln
*clefG2
=1
2rAyy 2reyy 2ee
4rdyy 4rayy 4aa
4rayy 4reeyy 4eee
2reeyy 2rbbyy 2bbb
=
*-
</script>

Harmonic symbols can be added to the sounding note in such cases:

{% include verovio.html
	source="fingharmring"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fingharmring">
**kern
*Ivioln
*clefG2
=1
2rAyy 2reyy 2eeo
4rdyy 4rayy 4aao
4rayy 4reeyy 4eeeo
2reeyy 2rbbyy 2bbbo
=
*-
</script>

Adding `o` to the sounding fingered harmonic pitch is useful
for analytic purposes, and it can be hidden by adding a single
`y` immediately after the `o`:

{% include verovio.html
	source="fingharmnoring"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fingharmnoring">
**kern
*Ivioln
*clefG2
=1
2rA 2re 2eeoy
4rd 4ra 4aaoy
4ra 4ree 4eeeoy
2ree 2rbb 2bbboy
=
*-
</script>


# Fourth harmonic #

Fourth harmonics are created by touching the string a perfect
forth above the stopped string, producing a sounding note
two octaves above the stopped string.


{% include verovio.html
	source="fourth"
	humdrum-min-height="200px"
	scale="55"
%}
<script type="text/x-humdrum" id="fourth">
**kern
*Ivioln
*clefG2
=1
2rB 2re- 2bboy
2rc 2rf 2cccoy/
2rd 2rg 2dddoyy
=
*-
</script>


