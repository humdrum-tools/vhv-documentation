---
title: Tremolos
lang: en
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







