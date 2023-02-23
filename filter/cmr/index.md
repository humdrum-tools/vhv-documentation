---
title: cmr filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 4 May 2022
last_updated:
ref: filters-cmr
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/cmr/index.html
---

The `cmr` filter marks *conspicuous melodic repetitions*,
particularly for use with vocal music from the Renaissance.

<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}

A "Conspicuous Melodic Repetition" is defined as the repetition of
a pitch at least three times within six whole notes' duration.  One
of the repeated pitches must be a local melodic high (or low) note
and be either syncopated or approached by a leap.  The other repeated
notes must be at least metrically accented.


<a name="option-l"></a>
<a name="option-L"></a>
## Local melodic maximums ##

Identifying local high notes is the first step in identifying a
CMR.  These local maximum are defined as having a higher pitch
than the note immediately preceding or following the peak note.
In the example below, green notes mark local maximums:

{% include verovio.html
	source="leap"
	scale="50"
	pageWidth="1300"
	humdrum-min-height="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="leap">
**kern
*clefGv2
*k[]
*M2/1
*met(C|)
=10
1A
2r
2e
=11
1fN
1e
=12
1c
1fN
=13
1.e
2e
=14
1fN
1e
=15
[0c
=16
0c]
=
*-
!!!RDF**kern: N = marked note, color=limegreen
!!!verovio: spacingLinear 0.3
!!!verovio: spacingNonLinear 0.4
</script>

{% include display-vhv-link.html link="https://verovio.humdrum.org/?file=jrp/Jos/Jos2819-Je_ris.krn&filter=cmr%20-lp" %}

The `-l` option can be added to highlight the local maximum pitches,
while the `-L` option can be used to mark only the local maximum
pitches without further analysis to identify CMRs.


## Syncopation or leaps ##

The next criteria to identify a CMR is that a local maximum must
be additionally accentuated by either being syncopated or 
preceded by a leap&mdash;a melodic interval greater than a second.


<a name="option-e"></a>
<a name="option-E"></a>
### leaps ###

The `-e` or `-E` option highlights leaps preceding local maximum pitches.

{% include verovio.html
	source="local"
	scale="50"
	pageWidth="1300"
	humdrum-min-height="200px"
	tabsize="8"
%}
<script type="text/x-humdrum" id="local">
**kern
*clefGv2
*k[]
*M2/1
*met(C|)
=10
1A
2r
2e
=11
1fN
1e
=12
1cK
1fN
=13
1.e
2e
=14
1fN
1e
=15
[0c
=16
0c]
=
*-
!!!RDF**kern: N = marked note, color=limegreen
!!!RDF**kern: K = marked note, color=goldenrod
!!!verovio: spacingLinear 0.3
!!!verovio: spacingNonLinear 0.4
</script>



<a name="option-s"></a>
<a name="option-S"></a>
### syncopations ###



