---
title: Repetition symbols
lang: en es
ref: humdrum-repetition-symbols
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum repetition symbols
creation_date: 7 Mar 2019
translation_date: 10 Aug 2021
last_updated: 7 Mar 2019
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode repetition symbols in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/repetition-symbols/index-ES.html
---

Repetition are represented in `**kern` by placing the tandem interpretations
`*rep` and `*Xrep` before and after the group of notes to repeat.  Depending
on the type of replacement, the visual aspect of the repetition will be
chosen based on the context in which it is found.


## Measure-level repetitions ##


{% include verovio.html
	source="repmeasure"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="repmeasure">
**kern
*M3/4
=1
4c
4d
4e
=2
*rep
4c
4d
4e
*Xrep
=3
4e
4d
4c
=4
*rep
4e
4d
4c
*Xrep
=5
*rep
4e
4d
4c
*Xrep
=
*-
</script>


## Half-measure repetitions ##

{% include verovio.html
	source="halfmeasure"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="halfmeasure">
**kern
*M4/4
=1
8cL
8dJ
16gLL
16f
16e
16dJJ
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
=
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
=
2c;
=
*-
</script>



## Beat repetitions ##

{% include verovio.html
	source="beat"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="beat">
**kern
*M4/4
=1
8cL
8dJ
*rep
8cL
8dJ
*Xrep
*rep
8cL
8dJ
*Xrep
*rep
8cL
8dJ
*Xrep
=2
8dL
8cJ
*rep
8dL
8cJ
*Xrep
8cL
8dJ
*rep
8cL
8dJ
*Xrep
=2
=
*-
</script>


The number of slashes in a beat repetition symbol is determined by the 
duration of the individual notes in the repetition:


{% include verovio.html
	source="beat2"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="beat2">
**kern
*M6/4
=1
8cL
8dJ
*rep
8cL
8dJ
*Xrep
16cLL
16d
16e
16fJJ
*rep
16cLL
16d
16e
16fJJ
*Xrep
32cLLL
32dL
32eJ
32fJJ
32gLL
32aL
32bJ
32ccJJJ
*rep
32cLLL
32d
32e
32fJJ
32gLL
32a
32b
32ccJJJ
*Xrep
=
*-
</script>


Examples of mixed-rhythm beat repetitions:

{% include verovio.html
	source="mixed"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="mixed">
**kern
*M4/4
=1
8.cL
16dJ
*rep
8.cL
16dJ
*Xrep
16eL
16d
8cJ
*rep
16eL
16d
8cJ
*Xrep
=2
1c
=
*-
</script>


## Removing repetition symbols ##

If you want to switch display styles from repetition symbols
to fully written-out music, you can use the
[shed](/filter/shed) filter to remove the `*rep` markers before
printing:


{% include verovio.html
	source="remove"
	humdrum-min-width="280px"
	scale="75"
%}
<script type="application/json" id="remove">
**kern
*M4/4
=1
16cLL
16e
16g
16eJJ
*rep
16cLL
16e
16g
16eJJ
*Xrep
*rep
16cLL
16e
16g
16eJJ
*Xrep
=
*-
</script>

{% include verovio.html
	source="remove2"
	humdrum-min-width="280px"
	scale="75"
%}
<script type="application/json" id="remove2">
!!!filter: shed -e 's/^X?rep$//I'
**kern
*M4/4
=1
16cLL
16e
16g
16eJJ
*rep
16cLL
16e
16g
16eJJ
*Xrep
*rep
16cLL
16e
16g
16eJJ
*Xrep
=
*-
</script>





## Error checking ##

Note that repetition symbols will not be checked for accuracy.
The music inside of the repetition symbol markers should match
the music preceding it that is being repeated; however, if this
is not the case, the repetition symbol will still be generated.


{% include verovio.html
	source="bad"
	scale="75"
%}
<script type="application/json" id="bad">
**kern
*M4/4
=1
4c
4g
*rep
4d
4a
*Xrep
=
*-
</script>



