---
title: autocadence filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 19 Apr 2025
last_updated: 19 Apr 2025
ref: filters-autocadence
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/autocadence/index.html
---

{% include filter-options.html file="options.aton" lang="EN" %}

The autocadence filter identifies cadences in sixteenth-century music.


## Default behavior ##

The default behavior is to display suspensions/agents in red above each
staff.  Vocal functions at the cadence are shown in blue above final note
of the cadence.

{% include verovio.html
	source="basic-example"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="basic-example">
!!!filter: autocadence
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>

<a name="option-S"></a>
## Hide suspension/agent labels ##

The `-S` option will suppress display of the suspension/agent labels:

{% include verovio.html
	source="suppress-suspensions"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="suppress-suspensions">
!!!filter: autocadence -S
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>

<a name="option-c"></a>
## Color cadential definition ##

The `-c` option will color the notes involved in definiing a cadential
voice pair:

{% include verovio.html
	source="color-cadence"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="color-cadence">
!!!filter: autocadence -c
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>


<a name="option-color"></a>
The `--color` option can be used to change the color for cadential definition
notes:

{% include verovio.html
	source="color-cadence-change"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="color-cadence-change">
!!!filter: autocadence -c --color limegreen
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>


<a name="option-color"></a>
The `--color` option can be used to change the color for cadential definition
notes:



<a name="option-i"></a>
## Intervals ##

To display the underlying interval analysis for cadence definitions, use `-i`:


{% include verovio.html
	source="cadence-intervals"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="cadence-intervals">
!!!filter: autocadence -c -i
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>

<a name="option-I"></a>
The `-I` option is similar to `-i`, but final cadential analysis is not done.

{% include verovio.html
	source="cadence-intervals-only"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="cadence-intervals-only">
!!!filter: autocadence -c -I
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>

<a name="option-i"></a>
The `-I` option is similar to `-i`, but final cadential analysis is not done.




<a name="option-l"></a>
## Lowest note dissonance analysis ##

By default, suspensions will be used to label dissonances for the 
cadential definitions.  Use the `-l` option to use the lowest note
to label dissonances:

{% include verovio.html
	source="lowest-intervals"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="lowest-intervals">
!!!filter: autocadence -c -i -l
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>


<a name="option-d"></a>
## Append cadential definition index ##

In order to identify which cadential definition was used to
mark a cadential pair, add the `-d` option:

{% include verovio.html
	source="cadential-index"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="cadential-index">
!!!filter: autocadence -c -d
**kern	**kern
*clefF4	*clefG2
*M2/1	*M2/1
1G	2e
.	1g
1A	.
.	2f#
=	=
1G	1g
==	==
*-	*-
</script>

<a name="option-r"></a>
The `-r` option will show all a list of all of the cadential definitions 
found in the score.


score


