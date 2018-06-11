---
title: Cue-sized notes
lang: en
ref: humdrum-cues
author: Craig Stuart Sapp
translator: 
keywords: humdrum cue
creation_date: 27 Mar 2018
translation_date: 
last_updated: 27 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode cue-sized notes in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/cues/index.html
---

Cue-sized notes are smaller than regular notes, similar to grace
notes; however, unlike grace notes, cue-sized notes possess non-zero
score durations.  Cue-sized notes can be encoded in two ways within
`**kern` spines.  For occasional cue-sized notes, an RDF record can
be added to mark individual notes as being cue-sized:


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
.	8aNJ
*v	*v
4b
=
*-
!!!RDF**kern: N = cue size
</script>


For generating a longer sequence of cue-sized notes, a second method using `*cue` 
and `*Xcue` tandem interpretations can be used to turn on/off cue-size:

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


The `*cue` and `*Xcue` markers only apply to a specific subspine of music, so one 
subspine can be cue sized while another is not.  This is useful for adding 
cues to orchestra parts.


{% include verovio.html
	source="cue3"
	humdrum-min-height="710px"
	scale="55"
%}
<script type="application/json" id="cue3">
**kern
*M4/4
=1
*^
*	*cue
!	!LO:TX:b:t=vlas.
1r	4e
.	4f
.	4e
.	4c
*	*Xcue
=2	=2
*cue	*
!LO:TX:a:t=vlns.	!
4ee	1r
4ff	.
4ee	.
4cc	.
*Xcue	*
=3	=3
*cue	*
8ffL	2r
8eeJ	.
8ddL	.
8ccJ	.
!	!LO:TX:a:B:t=solo
2ryy	16ffLL
.	16ee
.	16dd
.	16ccJJ
.	16bLL
.	16a
.	16g
.	16fJJ
*Xcue	*
*v	*v
=
*-
</script>


