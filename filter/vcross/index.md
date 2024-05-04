---
title: vcross filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 28 April 2024
last_updated: 28 April 2024
ref: filters-vcross
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/vcross/index.html
---

The vcross filter highlights voice crossings between adjacent staves in a score.

* Red = a lower voice note is higher than currently sounding note in adjacent staff above.
* Blue = a higher voice note is lower than currently sounding note in adjacent staff below.
* Green = two adjacent staves have the same pitch.
	


## Example ##


{% include verovio.html
	source="cross1"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="800"
%}
<script type="text/x-humdrum" id="cross1">
!!!filter: vcross
**kern	**kern	**kern
*part3	*part2	*part1
*staff3	*staff2	*staff1
*clefF4	*clefG2	*clefG2
*k[]	*k[]	*k[]
*C:	*C:	*C:
*M3/8	*M3/8	*M3/8
=32	=32	=32
8.GL	(8ccL	8ddL
.	8b)	(8g
16FL	.	.
16E	8eeJ	8ccJ)
16CJJ	.	.
=33	=33	=33
8.FL	(8aL	8ccL
.	8cc)	(8a
16EL	.	.
16F	8ffJ	8ddJ)
16DJJ	.	.
=34	=34	=34
8.GL	(8bL	8ddL
.	8dd)	(8b
16FL	.	.
16G	8ggJ	8eeJ)
16EJJ	.	.
=35	=35	=35
8.AL	(8ccL	8eeL
.	8ee)	(8cc
16GL	.	.
16A	8aaJ	8ffJ)
16FJJ	.	.
=36	=36	=36
8.GL	8.ddL	(8bL
.	.	8g)
16FL	16bk	.
16E	[8ccJ	[8eeJ
16CJJ	.	.
=37	=37	=37
16FLL	16ccLL]	16eeLL]
16D	16ddJ	16ffJ
16G	8.b	8.dd
16F	.	.
16G	.	.
16GGJJ	16ccJk	16ccJk
=38	=38	=38
8.CL>	4cc	(8ccL
.	.	8g)
16DL	.	.
16E	8r	8ccJ
16CJJ	.	.
=	=	=
*-	*-	*-
!!!RDF**kern: > = above
!!!RDF**kern: < = below
</script>


<a target="_blank" href="https://verovio.humdrum.org/?file=nifc/popc2/pl-wn/pl-wn--mus-iii-86-058_zelenski-wladyslaw--piesn-zeglarzy-schifferlied-op-34-nr-1.krn&filter=vcross">Example showing shift between four- and two-part textures</a>.


<a target="_blank" href="https://verovio.humdrum.org/?file=chorales/chor182.krn&filter=vcross">Voice crossing in a Bach chorale</a>.


<a target="_blank" href="https://verovio.humdrum.org/?file=1520s/Ver2001-Sancta_Maria_succurre_miseris.krn&filter=vcross">Voice crossing in Renaissance music</a>.

<a target="_blank" href="https://verovio.humdrum.org/?file=vivaldi/op01/vivaldi-op01n04m02.krn&filter=vcross">Voice crossing betwen first and second violins in Vivaldi, Op. 1</a>

<a target="_blank" href="https://verovio.humdrum.org/?file=chopin-first-editions/074-1-G-002.krn&filter=vcross">Duplication of vocal melody in piano part</a>.



