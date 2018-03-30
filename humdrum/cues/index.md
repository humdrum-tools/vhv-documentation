---
title: Cue-sized notes
author: Craig Stuart Sapp
keywords: humdrum cue
creation_date: 27 Mar 2018
last_updated: 27 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode cue-sized notes in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/cues/index.html
---

Cue-sized notes can be encoded in two ways within `**kern` spines.  Individual
notes can be marked as cue-sized by using an `RDF` record:


{% include verovio.html
	source="cue1"
	humdrum-min-height="210px"
	scale="55"
%}
<script type="application/json" id="cue1">
**kern
4e
*^
4g	8gN\L
.	8aN\J
*v	*v
4b
=
*-
!!!RDF**kern: N = cue size
</script>


The second method of indicating cue notes is more suitable when 
several notes within a layer should be in cue size.  In this case
place the `*cue` interpretation before the first note, and `*Xcue`
after the last note:

{% include verovio.html
	source="cue2"
	humdrum-min-height="580px"
	tabsize="12"
	scale="55"
%}
<script type="application/json" id="cue2">
**kern	**kern
*clefF4	*clefG2
*M3/4	*M3/4
=	=
*	*Xtuplet
*	*cue
*	*rscale:2
4G 4c 4f	(>20ddL>
.	20ee
.	20dd
.	20cc#
.	20dd
4G 4B 4f	20dd#
.	20ee
.	20ff
.	20ff#
.	20gg
4G 4B 4f	20gg#
.	20bb
.	20aa
.	20ggn
.	20ffnJ)
*	*Xcue
*	*rscale:1
=	=
4G 4B 4e	2.ee
4G 4B 4e	.
4G 4B 4e	.
=	=
*-	*-
!!!RDF**kern: > = above
</script>




