---
title: double filter
lang: en
ref: filters-double
author: Craig Stuart Sapp
creation_date: 09 May 2022
last_updated: 09 May 2022
translator:
translation_date:
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/double/index.html
---

The double filter doubles rhythmic values in a score.  It mostly
reversed the effect of the [half](/filter/half) filter.


## Basic usage ##


Here is some example music:

{% include verovio.html
	source="plain"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="plain">
**kern
*M4/4
=1
4c
4d
4e
4f
=2
1g
=3
8fL
8e
8d
8cJ
=
2B
2e
=
1d
==
*-
</script>


The double filter will convert the time signature to 4/2 and double
rhythms, such as half notes to whole notes:

{% include verovio.html
	source="double"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="double">
!!!filter: double
**kern
*M4/4
=1
4c
4d
4e
4f
=2
1g
=3
8fL
8e
8d
8cJ
=
2B
2e
=
1d
==
*-
</script>


The filter can be applied multiple times, for example to
quadruple notes durations from their original durations:

{% include verovio.html
	source="doubledouble"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="doubledouble">
!!!filter: double | double
**kern
*M4/4
=1
4c
4d
4e
4f
=2
1g
=3
8fL
8e
8d
8cJ
=
2B
2e
=
1d
==
*-
</script>



