---
title: dissonant filter
author: ["Craig Sapp", "Alex Morgan"]
creation_date: 29 May 2017
last_updated: 29 May 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "The dissonant filter labels the function of non-harmonic tones in contrapuntal textures."
permalink: /filters/dissonant/index.html
---

The dissonant filter automatically labels the function
of non-harmonic notes in contrapuntal textures.  Each input `**kern`
spine is expected to be monophonic and have no subspine branching.
If there are chords in the music, the first note of the chord is
used, and secondary subspines will be ignored.

Below is an example of the dissonant filter in action.  To apply the filter to 
a file, include the line `!!!filter: dissonant` anywhere in the file.  The label
for each voice will be inserted in spines immediately to the left of each
`**kern` spine.  In the following display the labels are shown above the notes
to which they apply.  `P` means a rising passing tone and `p` means a lower
passing tone.  See the complete list of label abbreviations further below.

{% include verovio.html
	source="josex"
	scale="40"
	spacingStaff="4"
	spacingSystem="4"
	pageWidth="1450"
	tabsize="10"
%}

<script type="application/json" id="josex">!!!filter: dissonant
**kern	**kern	**kern
*I"Bassus	*I"Tenor	*I"Discantus
*I'B	*I'T	*I'D
*clefF4	*clefGv2	*clefG2
*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=1-	=1-	=1-
0r	0A	0e
=2	=2	=2
0r	1.A	1.e
.	4G	2f
.	4F	.
=3	=3	=3
0r	1E	1g
.	[1F	[1a
=4	=4	=4
0A	2F]	2a]
.	2E	2g
.	2D	2f
.	4C	4e
.	4BB	4d
=5	=5	=5
0A	1AA	1c
.	4AA	1cc
.	4BB	.
.	4C	.
.	4D	.
=6	=6	=6
1G	1E	2.b
.	.	4a
1A	1AA	1cc
=7	=7	=7
0F	0A	4cc
.	.	4b
.	.	4a
.	.	4g
.	.	1a
=8	=8	=8
0E	1B	0g
.	[1c	.
=9	=9	=9
0r	2c]	1r
.	4B	.
.	4A	.
.	1B	1g
=10	=10	=10
0r	1.A	1a
.	.	1cc
.	4G	.
.	4F	.
=11	=11	=11
0G	0E	1b
.	.	4b
.	.	4a
.	.	4g
.	.	4f
=12	=12	=12
0G	1r	1e
.	1B	1d
=13	=13	=13
1F	1A	1d
1G	[1B	[1e
=14	=14	=14
0E	2B]	2e]
.	2.G	2f
.	.	[1g
.	4A	.
.	4B	.
.	4c	.
=15	=15	=15
0D	2d	2g]
.	1c	4f
.	.	4e
.	.	1f
.	2B	.
=16	=16	=16
0r	2.c	0e
.	4B	.
.	2G	.
.	[2A	.
=17	=17	=17
0r	2A]	1r
.	4G	.
.	4F	.
.	1E	1b
=18	=18	=18
0F	1r	1.a
.	1D	.
.	.	4b
.	.	4cc
=19	=19	=19
0F	4D	1dd
.	4E	.
.	4F	.
.	4G	.
.	1A	[1cc
=20	=20	=20
1E	2G	2cc]
.	1c	4b
.	.	4a
1F	.	2a
.	2A	2cc
=	=	=
*-	*-	*-
!!!RDF**kern: i=editorial accidental
</script>

Try editing the above Humdrum textual score to generate various types of dissonances.

## Dissonant function labels ##

<style>

.dense td { 
	padding-top: 1px;
	padding-bottom: 1px;
	margin-top: 0;
	margin-bottom: 0;
}

.twocol td:first-child { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(2) { width: 40%; vertical-align: middle}
.twocol td:nth-child(3) { width: 10%; text-align: center; vertical-align: middle}
.twocol td:nth-child(4) { width: 40%; vertical-align: middle}

.onecol td:first-child { width: 20%; text-align: center; vertical-align: middle}
.onecol td:nth-child(2) { width: 80%; vertical-align: middle}



</style>

<table class="dense twocol">
<tr><th>Label</th><th> Meaning</th>                             <th>Label</th><th> Meaning</th>                                 </tr>
<tr><td> P </td><td> rising passing tone</td>                   <td> p </td>  <td> downward passing tone</td>                   </tr>
<tr><td> N </td><td> upper neighbor</td>                        <td> n </td>  <td> lower neighbor</td>                          </tr>
<tr><td> E </td><td> upper &eacute;chapp&eacute;e</td>                        <td> e </td>  <td> lower &eacute;chapp&eacute;e</td>                          </tr>
<tr><td> C </td><td> ascending short nota cambiata</td>         <td> c </td>  <td> descending short nota cambiata</td>          </tr>
<tr><td> K </td><td> ascending long nota cambiata</td>          <td> k </td>  <td> descending long nota cambiata</td>           </tr>
<tr><td> I </td><td> incomplete anterior upper neighbor</td>    <td> i </td>  <td> incomplete anterior lower neighbor</td>      </tr>
<tr><td> J </td><td> incomplete posterior upper neighbor</td>   <td> j </td>  <td> incomplete posterior lower neighbor</td>     </tr>
<tr><td> A </td><td> rising anticipation</td>                   <td> a </td>  <td> descending anticipation</td>                 </tr>
<tr><td> s </td><td> suspension</td>                            <td> G </td>  <td> suspension agent</td>                        </tr>
<tr><td> F </td><td> fake suspension approached by step up</td> <td> f </td>  <td> fake suspension approached by step down</td> </tr>
<tr><td> o </td><td> suspension ornament</td>                   <td> r </td>  <td> suspension repeated note</td>                </tr>
<tr><td> h </td><td> chanson idiom</td>                         <td> Q </td>  <td> dissonant third quarter</td>                 </tr>
<tr><td> Z </td><td> unknown dissonance, 2nd or 7th interval</td>      <td> z </td ><td> unknown dissonance, 4th interval</td></tr>
</table>

The `-u` option (*undifferentiate*) collapses up/down subcategorizations into a single case designated with an uppercase letter:

<table class="dense onecol">
<tr><th>Label</th><th> Meaning</th></tr>
<tr><td> P </td><td> passing tone</td></tr>
<tr><td> N </td><td> neighbor</td></tr>
<tr><td> E </td><td> &eacute;chapp&eacute;e</td></tr>
<tr><td> C </td><td> short nota cambiata</td></tr>
<tr><td> K </td><td> long nota cambiata</td></tr>
<tr><td> I </td><td> incomplete anterior neighbor</td></tr>
<tr><td> J </td><td> incomplete posterior neighbor</td></tr>
<tr><td> A </td><td> anticipation</td></tr>
<tr><td> Q </td><td> dissonant third quarter</td></tr>
<tr><td> S </td><td> suspension</td></tr>
<tr><td> F </td><td> fake suspension</td></tr>
<tr><td> G </td><td> suspension agent</td></tr>
<tr><td> O </td><td> suspension ornament</td></tr>
<tr><td> R </td><td> suspension repeated note</td></tr>
<tr><td> H </td><td> chanson idiom</td></tr>
<tr><td> Z </td><td> unknown dissonance</td></tr>
</table>


### Passing notes (P, p) ###

{% include verovio.html
	source="passing"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="passing">**kern	**kern
*M2/4	*M2/4
4C	8cL
.	8dJ
4AA	4e
=2	=2
4FF	8fL
.	8eJ
4GG	4d
==	==
*-	*-
!!!filter: dissonant
</script>

### Neighboring notes (N, n) ###

{% include verovio.html
	source="nei"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="nei">**kern	**kern
*M2/4	*M2/4
4C	8ccL
.	8ddJ
4AA	4cc
=2	=2
4GG	8bL
.	8aJ
4EE	4b
==	==
*-	*-
!!!filter: dissonant
</script>

###  &Eacute;chapp&eacute;e notes (E, e) ###

{% include verovio.html
	source="chap"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="chap">**kern	**kern
*clefF4	*clefG2
*M2/4	*M2/4
4F	8aL
.	8gJ
4E	4cc
=2	=2
4F	8aL
.	8bJ
4G	4g
==	==
*-	*-
!!!filter: dissonant
</script>

###  Cambiatas notes (C, c, K, k) ###

{% include verovio.html
	source="camb_dn"
	scale="60"
	pageWidth="1000"
	tabsize="10"
	spacingLinear="0.15"
	spacingNonLinear="0.50"
%}
<script type="application/json" id="camb_dn">**kern	**kern
*clefF4	*clefG2
*M3/2	*M3/2
2G	2.g
2E	.
.	4f
2G	2d
=2	=2
2G	2.g
2E	.
.	4f
2G	4d
.	4e
==	==
*-	*-
!!!filter: dissonant
</script>

{% include verovio.html
	source="camb_up"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="camb_up">**kern	**kern
*k[b-]	*k[b-]
*M4/2	*M4/2
2B-	2.d
2G	.
.	1e
2B-	2g
2C	2a
=2	=2
2B-	2.d
2G	.
.	1e
2B-	2g
2A	2f
==	==
*-	*-
!!!filter: dissonant
</script>



###  Incomplete neighbors (I, i, J, j) ###

###  Anticipations (A, a) ###

###  Suspensions (s, G, F, f, r, o) ###

### Dissonant third-quarter notes (Q) ###

### Chanson idiom (h) ###

### Unknown dissonances (Z, z) ###



## URL filtering of repertories ##

The dissonant tool can be used with available repertories by adding the
filter to the URL for the works, such as with the Tasso in Music Project:

[http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant)

To remove lyric text from analysis results, use the filter: `extractx -i kern | dissonant`:

[http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant)


## JRP dissonant tool ##

Work pages on the Josquin Research Project website have links to
VHV for the current work to view the dissonant labeling analysis.
For example the page:

[http://josquin.stanford.edu/work/?id=Jos2801](http://josquin.stanford.edu/work/?id=Jos2801)

Contains a button labeled "Dissonant" on the bottom left side of the page.  Clicking on that button will load
the score for the current page into VHV and do an online analysis of the dissonant labels.

### Dissonance symmaries ###

These are more useful for the command-line version of the tool, but can be viewed in VHV by typing command-c when the option is used.


The `-c` option displays a count of the different types of dissonances and total dissonances
within a work:


``` bash
humcat jrp://Jos2721 | dissonant -c
```
```
**dis	**sum	**v1	**v2	**v3
P	31	17	6	8
p	13	9	1	3
N	2	0	0	2
n	21	5	3	13
E	1	0	0	1
e	1	0	1	0
Q	1	0	1	0
s	6	1	2	3
G	11	5	4	2
h	1	0	0	1
Z2	1	1	0	0
Z7	1	0	0	1
*-	*-	*-	*-	*-
!!total_dissonances:	90
```

The `-u` option can also be used with the `-c` option to count dissonances without
subgrouping them by direction:

``` bash
humcat jrp://Jos2721 | dissonant -cu
```
```
**disu	**sum	**v1	**v2	**v3
P	44	26	7	11
N	23	5	3	15
E	2	0	1	1
Q	1	0	1	0
S	6	1	2	3
G	11	5	4	2
H	1	0	0	1
Z	2	1	0	1
*-	*-	*-	*-	*-
!!total_dissonances:	90
```

In this case the first spine data type is labeled as `**disu` to indicate the
undifferentiated directions for each category.



### References ###

Morgan, Alexander. "[Renaissance interval-succession theory: treatises and analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)". Ph.D. dissertation: McGill University: Canada; 2017.

