---
title: Embedded verovio options list
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 2 May 2022
last_updated:
ref: verovio options beamFrenchStyle
tags: [all, options]
sidebar: main_sidebar
verovio: "true"
keywords: embedded verovio options beamFrenchStyle
vim: ts=3
summary: 
permalink: /options/beamFrenchStyle/index.html
---

The `beamFrenchStyle` verovio option changes the attachment location of
stems on beams.  In the standard style, stems extend all of the way
to the furthest beam line.  In French style, the beam stops at the first
encountered line of the beam.

Also see [comprehensive list of options](/options/list).

Example without the `beamFrenchStyle` option:

{% include verovio.html
	humdrum-min-height="400px"
	humdrum-min-width="400px"
	source="optionoff"
	tabsize="17"
	scale="30"
	pageWidth="1200"
%}
<script type="application/x-humdrum" id="optionoff">
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[b-e-a-]	*k[b-e-a-]	*
*c:	*c:	*
*M4/4	*M4/4	*
*MM40	*MM40	*
=4	=4	=4
(4c	4f#/ 4an/ (4ee-/	fz
8Bn 8dL	8g 8ddL>	p
8B- 8c 8enJ)	8g 8cc 8eenJ)	<
8A-X' 8c' 8fn'	8a-' 8cc' 8ffn'	.
8r	[8aa-	fz
*	*Xtuplet	*
!	!	!LO:DY:b=2:rj
4BBB- 4BB-	(32aa-LLL]	fz
.	96ggL	.
.	96aa-	.
.	96bb-	.
.	96aa-	.
.	96gg	.
.	96ffJJJJ	.
.	64ee-LLLL	.
.	64dd	.
.	64cc	.
.	64b-JJJJ	.
*	*tuplet	*
*	*rscale:1/2	*
.	96a-LLLL	.
.	96g	.
.	96fni	.
.	96e-	.
.	96d	.
.	96f	.
.	96a-	.
.	96f	.
.	96dJJJJ	.
*	*rscale:1	*
=	=	=
*-	*-	*-
</script>



{% include verovio.html
	humdrum-min-height="400px"
	humdrum-min-width="400px"
	source="optionon"
	tabsize="17"
	scale="30"
	pageWidth="1200"
%}
<script type="application/x-humdrum" id="optionon">
!!!verovio: beamFrenchStyle
**kern	**kern	**dynam
*clefF4	*clefG2	*
*k[b-e-a-]	*k[b-e-a-]	*
*c:	*c:	*
*M4/4	*M4/4	*
*MM40	*MM40	*
=4	=4	=4
(4c	4f#/ 4an/ (4ee-/	fz
8Bn 8dL	8g 8ddL>	p
8B- 8c 8enJ)	8g 8cc 8eenJ)	<
8A-X' 8c' 8fn'	8a-' 8cc' 8ffn'	.
8r	[8aa-	fz
*	*Xtuplet	*
!	!	!LO:DY:b=2:rj
4BBB- 4BB-	(32aa-LLL]	fz
.	96ggL	.
.	96aa-	.
.	96bb-	.
.	96aa-	.
.	96gg	.
.	96ffJJJJ	.
.	64ee-LLLL	.
.	64dd	.
.	64cc	.
.	64b-JJJJ	.
*	*tuplet	*
*	*rscale:1/2	*
.	96a-LLLL	.
.	96g	.
.	96fni	.
.	96e-	.
.	96d	.
.	96f	.
.	96a-	.
.	96f	.
.	96dJJJJ	.
*	*rscale:1	*
=	=	=
*-	*-	*-
</script>





