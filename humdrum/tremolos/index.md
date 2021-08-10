---
title: Tremolos
lang: en es
ref: humdrum-tremolos
author: Craig Stuart Sapp
translator: 
keywords: humdrum tremolo
creation_date: 18 Mar 2018
translation_date: 
last_updated: 18 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode tremolos in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/tremolos/index.html
---

Tremolos are represented in `**kern` by encoding the individual notes
in the tremolo within a single beam group, and then adding a
`*tremolo` tandem interpretation before the beamed notes that should
be converted into a tremolo.

{% include verovio.html
	source="tremolo"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo">
**kern
*M3/4
=1
16eLL
16e
16e
16eJJ
*tremolo
16eLL
16e
16e
16eJJ
16fLL
16f
16e
16eJJ
=2
8fL
8f
8f
8f
8f
8fJ
*Xtremolo
=
*-
</script>

Use `*Xtremolo` to turn off tremolo conversion of beamed notes:

{% include verovio.html
	source="tremolooff"
	humdrum-min-height="340px"
	scale="75"
%}
<script type="application/json" id="tremolooff">
**kern
*M3/4
16eLL
16e
16e
16eJJ
*tremolo
16eLL
16e
16e
16eJJ
*Xtremolo
16fLL
16f
16e
16eJJ
=
*-
</script>



When `*tremolo` is active, only beamed groups that can convert into tremolos
will be converted into tremolos.  Other patterns of beamed notes will remain
unaffected.


{% include verovio.html
	source="tremolo3"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo3">
**kern
*M3/4
*tremolo
16eLL
16e
16e
16eJJ
16eLL
16f
16g
16fJJ
32fLL
32f
32f
32f
32e
32e
32e
32eJJ
=
*-
</script>


Tremolos also work with beamed chord notes


{% include verovio.html
	source="tremolo4"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo4">
**kern
*M3/4
16e 16g 16bLL
16e 16g 16b
16e 16g 16b
16e 16g 16bJJ
*tremolo
16e 16gLL
16e 16g
16e 16g
16e 16gJJ
16e 16g 16bLL
16e 16g 16b
16e 16g 16b
16e 16g 16bJJ
=
*-
</script>

## Fingered tremolos ##

The `*tremolo` interpretation can also reduce alternating notes into
tremolos:

{% include verovio.html
	source="tremolo5"
	humdrum-min-height="580px"
	scale="75"
%}
<script type="application/json" id="tremolo5">
**kern
*M3/4
=
16eLL
16g
16e
16gJJ
*tremolo
16eLL
16g
16e
16g
16e
16g
16e
16gJJ
=
16eLL
16g
16e
16g
16e
16g
16e
16g
16e
16g
16e
16gJJ
=
*-
</script>


Two-note tremolos also work with chords:

{% include verovio.html
	source="tremolo6"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo6">
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>



## Disabling tremolos ##

Tremolos can be disabled from notation rendering by using the
[shed](/filter/shed) filter:


{% include verovio.html
	source="remove1"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="remove1">
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>

{% include verovio.html
	source="remove2"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="remove2">
!!!filter: shed -e 's/^X?tremolo$//I'
**kern
*M3/4
*tremolo
16eLL
16g
16e
16gJJ
16e 16g 16bLL
16g 16b 16dd
16e 16g 16b
16g 16b 16ddJJ
16eLL
16g 16b 16dd
16e
16g 16b 16ddJJ
=
*-
</script>


## Tremolo filter ##

The tremolo filter can be used to add tremolo notes to a Humdrum
score that does not have expanded tremolos.  To expand a single
note into a tremolo, add the duration of the tremolo surrounded by
`@` markers after the note token(s):

{% include verovio.html
	source="tremolo1"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo1">
!!!filter: tremolo
**kern
*clefG2
*M4/4
=1
1c@16@
=2
2d@8@
2e@32@
=
*-
</script>

Scores should not be stored in compressed tremolo format, as the
`@` encoding is only intended to add tremolos to the score using
the tremolo filter.  Here is the result of compiling the filter:

{% include verovio.html
	source="tremolo1b"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo1b">
!!!Xfilter: tremolo
**kern
*clefG2
*M4/4
=1
*tremolo
16cLL
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16c
16cJJ
=2
8dL
8d
8d
8dJ
32eLLL
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32e
32eJJJ
*Xtremolo
=
*-
</script>


Two-note tremolos are encoded in a similar manner.  Place the
duration for the tremolo only on the first note of a two-note pair,
surrounded with two `@@` characters rather than one.  Each note of
the pair should posses one-half of the total duration of the tremolo.

{% include verovio.html
	source="tremolo2"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo2">
!!!filter: tremolo
**kern
*clefG2
*M4/4
=1
2c@@16@@
2d
=2
4d@@8@@L
4eJ
4e@@32@@L
4fJ
=
*-
</script>



The result of compiling the filter:

{% include verovio.html
	source="tremolo2b"
	humdrum-min-width="310px"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="tremolo2b">
!!!Xfilter: tremolo
**kern
*clefG2
*M4/4
=1
*tremolo
16cLL
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16d
16c
16dJJ
=2
8dL
8e
8d
8eJ
32eLLL
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32f
32e
32fJJJ
*Xtremolo
=
*-
</script>


