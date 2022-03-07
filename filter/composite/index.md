---
title: composite filter
lang: en es
ref: filters-composite
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
permalink: /filter/composite/index.html
---

The composite filter can be used to extract the composite rhythm of a multi-voices score or multi-part score.

Here is an example of a score with two parts:

{% include verovio.html
	source="twoparts"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="twoparts">
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>

Each part has a different rhythm.  The `composite` filter collapses the note attacks of each part into
a single rhythmic pattern.

{% include verovio.html
	source="composite"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="composite">
!!!filter: composite
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Placing composite rhythm below system ###

Use the `-p` option to place the composite rhythm staff below the existing musical system:

{% include verovio.html
	source="prepend"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="prepend">
!!!filter: composite -p
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Placing composite rhythm above system ###

Use the `-a` option to place the composite rhythm staff above the existing musical system:

{% include verovio.html
	source="append"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="append">
!!!filter: composite -a
**kern	**kern
*M4/4	*M4/4
4c	2c
4d	.
2e	4d
.	4e
=	=
*-	*-
</script>


### Beaming ### 

By default, the rhythms of the composite rhythm will not be beamed:

{% include verovio.html
	source="nobeam"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="nobeam">
!!!filter: composite -p
**kern	**kern
*M4/4	*M4/4
4c	2c
16dL	.
8d	.
16dJ	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


Add the `-b` option to beam the notes according to the time signature:

{% include verovio.html
	source="beam"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="200px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="beam">
!!!filter: composite -pb
**kern	**kern
*M4/4	*M4/4
4c	2c
16dL	.
8d	.
16dJ	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


### Grace notes ### 

Grace notes are included in the composite rhythm analysis:

{% include verovio.html
	source="grace"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="grace">
!!!filter: composite -pb
**kern	**kern
*M4/4	*M4/4
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


but grace notes can be removed from the composite rhythm analysis with the `-G` option:

{% include verovio.html
	source="nograce"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="nograce">
!!!filter: composite -pbG
**kern	**kern
*M4/4	*M4/4
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>


### Pitch of composite rhythm notes ###

The `--pitch` option can set the pitch of the composite note.

{% include verovio.html
	source="pitch"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="325px"
	humdrum-min-width="300px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="pitch">
!!!filter: composite -pbG --pitch f#
**kern	**kern
*k[f#]	*k[f#]
*M4/4	*M4/4
=1	=1
.	16qdL
.	16qdJ
4c	2c
16dL	.
8d	.
16dJ	.
8qf#	.
2e	8dL
.	8dJ
.	4e
=	=
*-	*-
</script>

