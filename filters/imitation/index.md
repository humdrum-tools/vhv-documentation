---
title: imitation filter
lang: en
ref: filters-imitation
author: "Craig Sapp"
translator: 
creation_date: 18 Jun 2017
translation_date: 
last_updated: 18 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "The imitation filter identifies modal melodic repetition between voices."
permalink: /filters/imitation/index.html
---

The imitation tool identifies repeated patterns betweeen voices.


{% include verovio.html
	source="ockex"
	scale="40"
	spacingStaff="4"
	spacingSystem="4"
	spacingLinear="0.05"
	pageWidth="1150"
	tabsize="10"
%}
<script type="application/x-humdrum" id="ockex">!!!filter: imitation
**kern	**kern
*clefGv2	*clefG2
*M3/1	*M3/1
*met(O)	*met(O)
*MM320	*MM320
=125	=125
[0c	0c
=126	=126
0c]	1r
.	1g
=127	=127
1r	1a
1G	1b
=128	=128
1A	2.cc
.	4b
1B-	1g
=129	=129
2.c	1r
4B-	.
1G	1dd
=130	=130
1r	2b
.	2g
1d	1a
=131	=131
2B-	1g
2G	.
1A	1cc
=132	=132
1G	1dd
1c	1ee
=133	=133
1d	2dd
.	1b
1e	.
.	2g
=134	=134
*-	*-
</script>


# Imitation summary #

Beneath the first note of each imitation pair, a
text string gives four pieces of information
about the imitation.  The four fields are separated
by colons, and each value is prefixed by a letter:

prefix | parameter meaning
=======|=================
n      | A unique enumeration ID for each imitation pairs within the score, starting at 1.
c      | The count of the number of notes in each sequence of the imitation pair.
d      | The duration to the other sequence in the imitation pair.  A positive value means that the imitation occurs after the given sequence, while a negative value means that the other imitation sequence comes before the current sequence.
i      | The interval of the imitation in diatonic steps.  Positive values means that the imitation in the other location is high in pitch than the current sequence, while a negative value means that the paired sequence is at a lower pitch.



