---
title: sab2gs filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 1 Apr 2024
last_updated: 1 Apr 2024
ref: filters-sab2gs
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/sab2gs/index.html
---

The sab2gs filter can be used convert SAB (or STB) arrangement of
parts on three staves into a two-staff grand staff arrangement.

The middle voice will be associated with the top staff.  To move
the middle voice to the bottom staff, add a `*clefF4` interpretation.
Then to move back to the top staff by using `*clefG2` in the middle
voice.

{% include verovio.html
	source="clef"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="clef">
**kern	**kern	**kern
*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4
=1	=1	=1
4C	4g	4ee
2E	8eL	4dd
.	8dJ	.
.	8cL	8ccL
*	*clefF4	*
.	16BL	8eeJ
.	16GJJ	.
4A	8AL	4ff
*	*clefG2	*
.	8aJ	.
=2	=2	=2
1c	1g	1ee
=	=	=
*-	*-	*-
!!!verovio: spacingStaff 8
</script>

{% include verovio.html
	source="clef2"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="clef2">
!!!filter: sab2gs
**kern	**kern	**kern
*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4
=1	=1	=1
4C	4g	4ee
2E	8eL	4dd
.	8dJ	.
.	8cL	8ccL
*	*clefF4	*
.	16BL	8eeJ
.	16GJJ	.
4A	8AL	4ff
*	*clefG2	*
.	8aJ	.
=2	=2	=2
1c	1g	1ee
=	=	=
*-	*-	*-
!!!verovio: spacingStaff 8
</script>

An alternate method that can be used by itself or by mixing with
the clef method: use `*down` to move the middle voice to the bottom
staff, and `*Xdown` to move back to the top staff.  This allows the
middle staff to have its own clefs in open-score format.

{% include verovio.html
	source="down"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="down">
**kern	**kern	**kern
*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4
=1	=1	=1
4C	4g	4ee
2E	8eL	4dd
.	8dJ	.
.	8cL	8ccL
*	*down	*
.	16BL	8eeJ
.	16GJJ	.
4A	8AL	4ff
*	*Xdown	*
.	8aJ	.
=2	=2	=2
1c	1g	1ee
=	=	=
*-	*-	*-
!!!verovio: spacingStaff 8
</script>

{% include verovio.html
	source="down2"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-height="250px"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="down2">
!!!filter: sab2gs
**kern	**kern	**kern
*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefG2
*M4/4	*M4/4	*M4/4
=1	=1	=1
4C	4g	4ee
2E	8eL	4dd
.	8dJ	.
.	8cL	8ccL
*	*down	*
.	16BL	8eeJ
.	16GJJ	.
4A	8AL	4ff
*	*Xdown	*
.	8aJ	.
=2	=2	=2
1c	1g	1ee
=	=	=
*-	*-	*-
!!!verovio: spacingStaff 8
</script>

Here is an example of processing a Bach three-part invention.  In
this case the bottom staff changes to `*clefG2`, requiring using
`*down` to move the middle voice to the bottom staff (although
`*clefF4` could be used, but it would not look good in open-score
format being displayed in the wrong clef.

{% include verovio.html
	source="sinfonia11"
	scale="40"
	pageWidth="1350"
	tabsize="10"
%}
<script type="text/x-humdrum" id="sinfonia11">
!!!filter: sab2gs
!!!COM: Bach, Johann Sebastian
!!!CDT: 1685/03/31-1750/07/28
!!!OTL: Sinfonia 11 in G minor
!!!SCA: BWV 797
**kern	**kern	**kern
*staff3	*staff2	*staff1
*I"	*I"	*I"
*clefF4	*clefG2	*clefG2
*k[b-e-]	*k[b-e-]	*k[b-e-]
*g:	*g:	*g:
*M3/8	*M3/8	*M3/8
*MM80	*MM80	*MM80
=1	=1	=1
4G	4.r	16r
.	.	16ddLL
.	.	16b-
.	.	16gJ
8E-	.	8ggJ
=2	=2	=2
4D	16r	4.ff
.	16aLL	.
.	16f	.
.	16dJ	.
8B-	[8ddJ	.
=3	=3	=3
4G	8.ddL]	4.ee-
.	16b-K	.
8A	[8ccJ	.
=4	=4	=4
16B-LL	8.ccL]	4.dd
16d	.	.
16B-	.	.
16GJ	16aK	.
[8gJ	8b-J	.
=5	=5	=5
8.gL]	[4.a	4cc
16enK	.	.
8f#XJ	.	8dd
=6	=6	=6
4g	16aLL]	8.b-L
.	16f#XJJ	.
.	[4g	.
.	.	16b-K
8c	.	8ee-J
=7	=7	=7
4d	4g]	8.aL
.	.	16b-K
8D	8f#X	8ccJ
!!LO:LB:g=original
=8	=8	=8
16GLL	4.g	4.b-
16D	.	.
16BB-	.	.
16GGJ	.	.
8GJ	.	.
=9	=9	=9
4.F	16r	[4bnm
.	16dLL	.
.	16Bn	.
*	*clefF4	*
.	16GJ	.
*	*clefG2	*
.	[8gJ	16bLL]
.	.	32aL
.	.	32bJJJ
=10	=10	=10
16E-LL	4.g]	8.ccL
16G	.	.
16E-	.	.
16CJ	.	16ddK
[8cJ	.	[8ee-J
=11	=11	=11
4c]	4f	16ee-LL]
.	.	16dd
.	.	16bn
.	.	16gJ
8Bn	8d	8ffJ
=12	=12	=12
[4.c	16r	[4.ee-
.	16gLL	.
.	16e-	.
.	16cJ	.
.	8b-J	.
=13	=13	=13
16cLL]	4.a	8.ee-L]
16c	.	.
16A	.	.
16FJ	.	16ddK
8e-J	.	[8ccJ
=14	=14	=14
8.dL	8.fL	16ccLL]
.	.	16ff
.	.	16dd
16gK	[8.b-J	16b-J
8e-J	.	8bb-J
!!LO:LB:g=original
=15	=15	=15
4f	4b-]	8.ddL
.	.	16ee-K
8F	8a	8ccJ
=16	=16	=16
16B-LL	4.b-	4.b-
16F	.	.
16D	.	.
16BB-J	.	.
8AJ	.	.
*	*clefF4	*
=17	=17	=17
4.G	16r	[4.bb-
.	16dLL	.
.	16B-	.
.	16GJ	.
.	8fJ	.
=18	=18	=18
8cL	[4.e-	16bb-]LL
.	.	16gg
8B-	.	16ee-
.	.	16ccJ
8cJ	.	8bb-J
=19	=19	=19
4.F	16e-LL]	[4.aa
.	16e-	.
.	16c	.
.	16AJ	.
.	8fJ	.
=20	=20	=20
8B-L	[4.d	16aaLL]
.	.	16ff
8A	.	16dd
.	.	16b-J
8B-J	.	8bb-J
=21	=21	=21
4.En	16dLL]	[4.gg
.	16d	.
.	16B-	.
.	16GJ	.
.	8enJ	.
!!LO:LB:g=original
=22	=22	=22
4.F	8c#XL	16ggLL]
.	.	16een
.	8A	16cc#X
.	.	16aJ
.	[8dJ	[8ffJ
=23	=23	=23
8GL	8dL]	16ffLL]
.	.	16dd
8A	8c#X	16b-
.	.	16gJ
8B-J	8dJ	[8eenJ
=24	=24	=24
[4.A	4c#Xm	16eeLL]
.	.	16g
.	.	16b-
.	.	16een
.	8d	16f
.	.	[16ddJJ
=25	=25	=25
4.A_	4en	16ddLL]
.	.	16cc#X
.	.	16een
.	.	16gg
.	8f	16dd
.	.	[16ffJJ
=26	=26	=26
4.A_	4g	16ffLL]
.	.	16een
.	.	16gg
.	.	16bb-
.	8f	16dd
.	.	[16aaJJ
=27	=27	=27
4.A_	4en	16aaLL]
.	.	16cc#X
.	.	16een
.	.	16gg
.	8d	16bn
.	.	[16ffJJ
=28	=28	=28
4.A]	4c#Xm	16ffLL]
.	.	16a
.	.	16cc#X
.	.	16een
.	8Bn	16g#X
.	.	16ddJJ
!!LO:LB:g=original
=29	=29	=29
8.AL	[4.A	16cc#XLL
.	.	16een
.	.	16cc#
16GL	.	16aJ
16F	.	8ggnJ
16EnJJ	.	.
=30	=30	=30
4D	16ALL]	4.ff
*	*clefG2	*
.	16a	.
.	16f	.
.	16dJ	.
8BB-	[8ddJ	.
=31	=31	=31
4GG	8.ddL]	4.ee-
.	16b-K	.
8AA	[8ccJ	.
=32	=32	=32
16BB-LL	8.ccL]	[4.dd
16D	.	.
16BB-	.	.
16GGJ	16aK	.
8GJ	8b-J	.
=33	=33	=33
8.EnL	4g	16ddLL]
.	.	16cc#X
.	.	16een
16enK	.	16ggJ
8dJ	[8f	8bb-J
=34	=34	=34
4c#X	16fLL]	8.aaL
.	16en	.
.	16c#X	.
.	16AJ	16eenK
8d	8dJ	8ffJ
=35	=35	=35
8B-L	8.fL	8.ddL
8G	.	.
.	16gK	16eenK
8AJ	8enJ	8cc#XJ
!!LO:LB:g=original
=36	=36	=36
16DLL	4d	4dd
16DD	.	.
16FF	.	.
16AA	.	.
16D	8r	8ff
16CnJJ	.	.
=37	=37	=37
16BBnLL	8r	[4.ff
16GG	.	.
16BB	16r	.
16D	16ddKL	.
16G	8bnJ	.
16FJJ	.	.
=38	=38	=38
16E-LL	8.gL	8.ffL]
16C	.	.
16E-	.	.
16G	16bnK	16ddK
16c	8ccJ	8ee-J
16B-JJ	.	.
=39	=39	=39
16ALL	[4.cc	[4.ee-
16F	.	.
16A	.	.
16c	.	.
16f	.	.
16e-JJ	.	.
*clefG2	*	*
=40	=40	=40
16dLL	8.ccL]	8.ee-L]
16B-	.	.
16d	.	.
16f	16aK	16ccK
16b-	[8b-J	[8ddJ
16aJJ	.	.
=41	=41	=41
4.g	8.b-L]	16ddLL]
.	.	16bb-
.	.	16gg
*	*down	*
.	16b-K	16ee-J
.	[8ee-J	[8cccJ
=42	=42	=42
4.f	8.ee-L]	16cccLL]
.	.	16aa
.	.	16ff
.	16aK	16ddJ
.	[8ddJ	[8bb-J
!!LO:LB:g=original
=43	=43	=43
4.e-	8.ddL]	16bb-LL]
.	.	16gg
.	.	16ee-
.	16gK	16ccJ
.	[8ccJ	8aaJ
=44	=44	=44
4.d	16ccLL]	4ff#X
.	16f#X	.
.	16a	.
.	16ccJ	.
.	[8b-J	8gg
=45	=45	=45
4.c	16b-LL]	8.ee-L
.	16e-	.
.	16g	.
.	16b-J	16ddK
.	[8a-XJ	8ccJ
=46	=46	=46
8.B-L	16a-LL]	8.ddL
.	16f#XJJ	.
.	[4g	.
16dK	.	16b-L
8cJ	.	16a
.	.	16ccJJ
=47	=47	=47
8.dL	4g]	16b-LL
.	.	16dd
.	.	16cc
16cK	.	16ee-
8dJ	8f#X	16dd
.	.	16aaJJ
*clefF4	*	*
*	*Xdown	*
=48	=48	=48
16GLL	4.g	[4.b-
!	!	!
16D	.	.
16BB-	.	.
16GGJ	.	.
8FJ	.	.
=49	=49	=49
[4.E-	8cL	16b-LL]
.	.	16g
*	*clefF4	*
.	8B-	16e-
.	.	16cJ
.	8cJ	8b-J
*	*clefG2	*
!!LO:LB:g=original
=50	=50	=50
16E-LL]	4.f	[4.a
16C	.	.
16AA	.	.
16FFJ	.	.
8FJ	.	.
=51	=51	=51
[4.D	8B-L	16aLL]
.	.	16f
*	*clefF4	*
.	8A	16d
.	.	16B-J
.	8B-J	8a-XJ
*	*clefG2	*
=52	=52	=52
16DLL]	[4.e-	[4.g
16BB-	.	.
16GG	.	.
16EE-	.	.
16GG	.	.
16BB-JJ	.	.
=53	=53	=53
4.C	4.e-]	16gLL]
.	.	16b-
.	.	16an
.	.	16cc
.	.	16f#X
.	.	[16aJJ
=54	=54	=54
4.BB-	4.d	16aLL]
.	.	16a
.	.	16g
.	.	16b-
.	.	16en
.	.	[16gJJ
=55	=55	=55
8.AAL	4c	16gLL]
.	.	16g
.	.	16f#X
16FF#XK	.	16aJ
8GGJ	8r	[8ccJ
=56	=56	=56
8.FF#XL	4.r	16ccLL]
.	.	16b-
.	.	16a
16AAK	.	16ccJ
8CJ	.	[8ee-J
*	*clefF4	*
!!LO:LB:g=original
=57	=57	=57
8DD	8r	16ee-LL]
.	.	16dd
[4D	8DL	16cc
.	.	16b-
.	8EnJ	16a
.	.	16gJJ
=58	=58	=58
4.D_	4F#X	16ccLL
.	.	16b-
.	.	16a
.	.	16g
.	8G	16f#X
.	.	16enJJ
=59	=59	=59
4.D_	4A	16dLL
.	.	16f#X
.	.	16a
.	.	16cc
.	8B-	16g
.	.	[16b-JJ
=60	=60	=60
4.D_	4c	16b-LL]
.	.	16a
.	.	16cc
.	.	16ee-
.	8B-	16g
.	.	[16ddJJ
=61	=61	=61
4.D_	4A	16ddLL]
.	.	16f#X
.	.	16a
.	.	16cc
.	8G	16en
.	.	[16b-JJ
=62	=62	=62
4.D]	4F#X	16b-LL]
.	.	16d
.	.	16f#X
.	.	16a
.	8En	16c#X
.	.	16gJJ
=63	=63	=63
16r	16r	[4f#X
*Xtuplet	*	*
!LO:N:vis=4.	!	!
[16%5D	16DLL	.
.	16F#X	.
.	16AJ	.
*	*clefG2	*
.	[8dJ	16f#LL]
.	.	16f#JJ
!!LO:LB:g=original
=64	=64	=64
8.DL]	8d]	16aLL
.	.	16ccJJ
.	8rA	[4ee-
16cL	.	.
16B-	8r	.
16AJJ	.	.
=65	=65	=65
4G	4.r	16ee-LL]
.	.	16dd
.	.	16b-
.	.	16gJ
8E-	.	8ggJ
=66	=66	=66
4D	16r	4.ff
.	16aLL	.
.	16f	.
.	16dJ	.
8B-	[8ddJ	.
=67	=67	=67
4G	8.ddL]	4.ee-
.	16b-K	.
8A	[8ccJ	.
=68	=68	=68
16B-LL	8.ccL]	4.dd
16d	.	.
16B-	.	.
16GJ	16aK	.
[8gJ	8b-J	.
=69	=69	=69
8.gL]	[4.a	4cc
16enK	.	.
8f#XJ	.	8dd
=70	=70	=70
4g	16aLL]	8.b-L
.	16f#XJJ	.
.	[4g	.
.	.	16b-K
8c	.	8ee-J
=71	=71	=71
4d	4g]	8.b-L
.	.	16ccK
8D	8f#X	8aJ
=72	=72	=72
4.GG;	4.g;	4.g;
==	==	==
*-	*-	*-
!!!system-decoration: [(s1,s2,s3)]
</script>


