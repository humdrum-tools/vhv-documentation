---
title: humdiff filter
lang: en
ref: filters-humdiff
author: Craig Stuart Sapp
translator: 
creation_date: 15 Sep 2019
translation_date: 
last_updated: 15 Sep 2019
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/humdiff/index.html
---

The humdiff filter can be used automatically mark differences between
two or more scores of the same length.

Here are two example scores:

{% include verovio.html
	source="score1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="265px"
%}
<script type="text/x-humdrum" id="score1">
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
</script>


And another score with some differences:

{% include verovio.html
	source="score2"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="250px"
%}
<script type="text/x-humdrum" id="score2">
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>


The `humdiff` filter can be given these two scores, and it will highlight the notes in the first score that
are different in the second score.  Here is an example of using the first score as a reference and highlighting
notes that are different in the second score:


{% include verovio.html
	source="humdiff1"
	scale="60"
	pageWidth="1450"
	tabsize="16"
	humdrum-min-height="525px"
%}
<script type="text/x-humdrum" id="humdiff1">
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>


By reversing the order of the scores, the second score example can be displayed with notes different
from the first score example highlighted in red:


{% include verovio.html
	source="humdiff2"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="525px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="humdiff2">
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
</script>


Notice that the `humdiff` filter is preceded by four `!!!!` marks rather than the typical three `!!!` for filters.  This is because the
filter operates on more than one data segment.



### Switching the order of inputs ###

The [chooser](/filter/chooser) filter can be used to re-order Humdrum data segments before processing with the humdiff filter.
Here is an example of switching the first and second segments before analyzing with humdiff:


{% include verovio.html
	source="chooser"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="550px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="chooser">
!!!!filter: chooser -s 2,1 
!!!!filter: humdiff
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
**kern
*M4/4
=1
4c
4d
4e
4g
=2
4f
2a
4cc
==
*-
</script>








