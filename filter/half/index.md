---
title: half filter
lang: en
ref: filters-half
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
permalink: /filter/half/index.html
---

The half filter reduced rhythmic values by one half.  The primary
use is for applying rhythmic reductions to modern editions of
mensural music.  This filter reverses changes made by the 
[double](/filter/double) tool.


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}


## Basic usage ##


Here is some example music in 2/1 representing original
mensuration rhythms:

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
*M2/1
=1
1c
1d
=2
0g
=3
4f
4e
4d
4c
2B
2e
=
0d
==
*-
</script>


The half filter will convert the time signature to 2/2 and reduce 
all rhythms by 1/2, such as whole notes to half notes:


{% include verovio.html
	source="half"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="half">
!!filter: half
**kern
*M2/1
=1
1c
1d
=2
0g
=3
4f
4e
4d
4c
2B
2e
=
0d
==
*-
</script>


The filter can be applied multiple times, for example to
shorten the notes to 1/4 of their original durations:

{% include verovio.html
	source="halfhalf"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="halfhalf">
!!!filter: half | half 
**kern
*M2/1
=1
1c
1d
=2
0g
=3
2f
2e
2d
2c
=
0d
==
*-
</script>



