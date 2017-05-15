---
title: Pedal marks
author: Craig Stuart Sapp
keywords: humdrum pedal marks
creation_date: 18 Mar 2017
last_updated: 18 Mar 2017
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode pedal marks in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/pedal_marks/index.html
---


Sustain pedal marks can be encoded in Humdrum `**kern` data by using
`*ped` to indicate a down-pedal mark and `*Xped` to indicate an
up-pedal mark:

{% include verovio.html
	source="pedal"
	tabsize="12"
	humdrum-min-height="600px"
%}

<script type="application/json" id="pedal">
**kern	**kern
*clefF4	*clefG2
*k[]	*k[]
*M3/4	*M3/4
=33	=33
*ped	*
4FF'	(8ccL
.	8ff
4A 4c 4f	8gg
.	8aa
4A 4c 4f	8ccc
.	8fffJ
*Xped	*
=34	=34
*ped	*
4BB'	8gggL
.	8aaa
4G 4d 4f	8ggg
.	8fff
4G 4d 4f	8eee
.	8dddJ)
*Xped	*
=35	=35
*ped	*
4C'	(12cccL
.	12ddd
.	12cccJ
4G 4c 4e	4gg')
4G 4c 4e	(8ggL
*Xped	*
.	8bbnJ
=36	=36
*ped	*
4F'	2aa
4A 4c 4f	.
4A 4c 4f	4ff)
.	.
*Xped	*
=37	=37
4A 4c 4e	(8ccL
.	8cccJ
4A 4c 4e	12bbL
.	12ccc
.	12bbJ
4A 4c 4f	8aaL
.	8ffJ
=38	=38
4B 4f	8dd'L)
.	8dd'J
.	(8qee/
4B 4f	4dd)
4c 4e	4cc^
=39	=39
*-	*-
</script>


Try adding or removing pedal up/down marks in the above Humdrum data to see how
the notation on the right changes.


Pedal marks can be added graphically in VHV by clicking on a note and 
pressing <span class="keypress">alt-p</span> to add a down-pedal mark or
<span class="keypress">alt-shift-P</span> to add an up-pedal mark.


