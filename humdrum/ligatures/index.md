---
title: Ligature and coloration brackets
lang: en
ref: humdrum-ligatures
author: Craig Stuart Sapp
translator: 
keywords: humdrum ligature coloration
creation_date: 18 Mar 2018
translation_date: 
last_updated: 18 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode ligature brackets in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/ligatures/index.html
---

Ligatures are are sequences of notes attached to each other
in mensural music.  When notating the music in modern notation,
typically a bracket will be placed over the separated notes to
indicate that the group of notes were originally notated in a
ligature.

Use `*lig` to start a ligature bracket, and `*Xlig` to end a
ligature bracket in **kern data:


{% include verovio.html
	source="ligature2"
	humdrum-min-height="400px"
	spacingNonLinear="0.55"
	spacingLinear="0.20"
	scale="55"
	url="https://digi.vatlib.it/view/MSS_Chig.C.VIII.234"
%}
<script type="application/json" id="ligature2">
**kern
*clefC3
*M2/1
*met(C|)
=
*lig
1d
1B
=
0c
=
0d
*Xlig
=
2e
2d
1B
=
0c
=
*-
</script>


## Coloration brackets ##

Coloration brackets can be displayed by using `*col` and `*Xcol` to mark the beginning and
ending of the coloration in an original mensuration notation of the score.  Below
is a mensural notation excerpt of Ockeghem's Missa Ecce ancilla domini, tenor part:

{% include image.html
	file="chigcvii8234-tenor.jpg"
	alt="Ockghem coloration example"
	caption="Ockeghem: Missa Ecce ancilla domini, Kyrie, Tenor part opening."
%}

The black notes are colored, so marked with open brackets in the modern notation equivalent below.


{% include verovio.html
	source="coloration2"
	humdrum-min-height="575px"
	spacingNonLinear="0.5"
	spacingLinear="0.1"
	scale="55"
%}
<script type="application/json" id="coloration2">
**kern
*clefC4
*M3/1
*met(O)
=9
[0.d
=
0.d]
=
*col
1c
1B
[1d
=
1d]
0d
*Xcol
=
1e
2d
2B
1c
=
1d
0d
=
[0.G
=
0.G]
=
*-
</script>

