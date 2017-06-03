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
.	1A	1cc
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
	scale="40"
	pageWidth="1100"
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
	scale="40"
	pageWidth="1100"
	tabsize="10"
%}
<script type="application/json" id="camb_up">**kern	**kern
*k[b-]	*k[b-]
*M4/2	*M4/2
2B-	2.d
2F	.
.	4e
2B-	2g
2C	2a
=2	=2
2B-	2.d
2F	.
.	4e
2B-	2g
2A	2f
==	==
*-	*-
!!!filter: dissonant
</script>



###  Incomplete neighbors (I, i, J, j) ###

###  Anticipations (A, a) ###

{% include verovio.html
	source="ant"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="ant">**kern	**kern
*clefG2	*clefG2
*M4/2	*M4/2
4g	2ee
4f	.
1f	4dd
.	4cc
.	4dd
.	4ee
2e	2ee
==	==
*-	*-
!!!filter: dissonant
</script>

###  Suspensions (s, G, r, o) ###

{% include verovio.html
	source="sus"
	scale="40"
	pageWidth="1100"
	tabsize="10"
%}
<script type="application/json" id="sus">**kern	**kern
*I"T	*I"D
*clefGv2	*clefG2
*M3/1	*M3/1
=36	=36
1E	1e
1F	1d
[1G	2e
.	[2g
=37	=37
1G]	2g]
.	1e
0F	.
.	4d
.	4c
.	1d
=38	=38
0.E	1e
.	2r
.	1g
.	2e
==	==
*-	*-
!!!filter: dissonant
</script>
A suspension consists of a voice that becomes dissonant either by sustaining or restriking a note before resolving the dissonance down by step. This sustained voice was refered to as the (*patient*) by Artusi, and it gets the `s` label at the moment of the dissonance. Another voice strikes a note that is dissonant against the suspended note, and this voice gets a `G` label for (*agent*). It is common to have more than one agent per suspension.

In Renaissance music with a ternary tactus, the dissonant portion of a suspension usually lands on the second beat of the tactus. So in order to detect ternary suspensions, like the example above taken from Obrecht's four-voice motet Mille quingentis, the definition of a suspension that we use allows the dissonance to be metrically strong or weak. Consonant suspensions are ignored.

{% include verovio.html
	source="rsus"
	scale="40"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="rsus">**kern	**kern
*clefGv2	*clefG2
*M4/2	*M4/2
2e	2g
2d	2.f
1c	.
.	4f
.	2e
=	=
1d	2f
.	2r
2e	1cc
2f	.
==	==
*-	*-
!!!filter: dissonant
</script>

We detect two types of dissonant suspension ornaments both of which occur during what would normally be the dissonant phase of the suspension. The first consists of a simple rearticulation of the suspended note before it resolves down by step. The reartuclated note is generally a quarter note and is labeled with an `r`. While this figure, shown above, does occur in tonal music there are almost no occurences of this in the entire JRP database of scores. This demonstrates how dissonance analysis can be used to inform the study of style change over time.

{% include verovio.html
	source="osus"
	scale="40"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="osus">**kern	**kern
*clefGv2	*clefG2
*M4/2	*M4/2
2e	2g
2d	2.f
1c	.
.	4d
.	2e
=	=
1d	2f
.	2r
2e	1cc
2f	.
==	==
*-	*-
!!!filter: dissonant
</script>

The second type of suspension ornamentation is when the suspended note skips a third down before resolving up by step to the note that would be the standard resolution of the suspension. This is labeled with an `o`, as shown above.

###  Fake Suspensions (F, f) ###

{% include verovio.html
	source="fsus"
	scale="40"
	pageWidth="1100"
	tabsize="10"
%}
<script type="application/json" id="fsus">**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1
=26	=26	=26	=26
2D\	0A	4d\]	2f/
.	.	4c\	.
2C/	.	2e-i\	1g
1D	.	[1d	.
.	.	.	2f#i/
=27	=27	=27	=27
1GG	0G	2d\]	0g
.	.	2.B-\	.
1r	.	.	.
.	.	4c\	.
.	.	2d\	.
==	==	==	==
*-	*-	*-	*-
!!!filter: dissonant
</script>

Sometimes the preparation of a suspension is itself dissonant like in the example above from the Kyrie of Mouton's Missa Da pacem. This is often refered to as a (*fake suspension*) though would more accurately be called a fake preparation. It is approached by step up or down and remains in place or is restruck to become the dissonant portion of a suspension. Since we know the suspension will generally resolve down by step, we use an uppercase `F` or lowercase `f` to convey whether the dissonance was approached by step up or down respectfully. Because this happens over a pedal, and an agent is also needed for the suspension, this is generally only found in three or more voices, though could happen in two voice if the pedal tone were rearticulated at the moment it serves as the agent of the suspension.

{% include verovio.html
	source="afsus"
	scale="40"
	pageWidth="1100"
	tabsize="10"
%}
<script type="application/json" id="afsus">**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M3/1	*M3/1	*M3/1	*M3/1
=9	=9	=9	=9
1C	0.c	1r	4a/
.	.	.	4b-\
.	.	.	2.cc\
1E	.	1g	.
.	.	.	4b-\
.	.	.	1b-
1F	.	2.f\	.
.	.	.	2a/
.	.	4e\	.
=10	=10	=10	=10
2.G\	0B-	4d\	1b-
.	.	4c\	.
.	.	2B-\	.
4F\	.	.	.
2D\	.	2F/	2r
2.E-i\	.	2G/	2.g/
.	1r	1B-	.
4D\	.	.	4f/
2BB-/	.	.	2d/
==	==	==	==
*-	*-	*-	*-
!!!filter: dissonant
</script>

Occasionally a fake suspension is preceded by an anticipation as in the example above taken from the same Mouton Kyrie. In this case the fake suspension label takes the same case as that of the anticipation.

### Dissonant third-quarter notes (Q) ###

{% include verovio.html
	source="d3q"
	scale="60"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/json" id="d3q">**kern	**kern
*clefG2	*clefG2
*M4/2	*M4/2
2f	1.a
2e	.
1d	.
.	4g
.	4f
==	==
*-	*-
!!!filter: dissonant
</script>

A dissonant third quarter, labeled `q` like the one shown above, is similar to a descending passing tone. It corresponds to a dissonance in the metric position of a weak minim that lasts only a quarter note. It is approached and left by step down and must be preceded by a note with a duration of at least a minim. 

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

Antila, Christopher, Alexander Morgan, et al. VIS Framework (version 3.0.3). Python. Montreal: McGill University, 2016.

Bent, Margaret. “Grammar of Early Music: Preconditions for Analysis.” In Tonal Structures in Early Music, edited by Cristle Collins Judd, 15-59. London: Garland Publishing, 1998.

Burmeister, Joachim. Musical Poetics. Translation by Benito Rivera. New Haven: Yale University Press, 1993. Originally published 1606.

Cohen, David. “Metaphysics, Ideology, Discipline: Consonance, Dissonance, and the Foundations of Western Polyphony.” Theoria 7: 1–86.

Conklin, Darrell, and Mathieu Bergeron, “Discovery of Contrapuntal Patterns.” In Proceedings of the International Society for Music Information Retrieval (2010): 201–206.

DeFord, Ruth. Tactus Mensuration, and Rhythm in Renaissance Music. Cambridge: Cambridge University Press, 2015.

Fuller, Sarah. “Contrapunctus Theory, Dissonance Regulation, and French Polyphony of the Fourteenth Century.” In Medieval Music in Practice: Studies in Honor of Richard Crocker, edited by Judith Peraino, 113–52. Middleton, Wisconsin: American Institute of Musicology, 2013.

———. “Organum – discantus – contrapunctus in the Middle Ages.” In The Cambridge History of Western Music Theory, edited by Thomas Christensen, 477–502. Cambridge: Cambridge University Press, 2002.

Jeppesen, Knud. Counterpoint: The Polyphonic Vocal Style of the Sixteenth Century. Translated by Glen Haydon. New York: Dover Publications, 1992 (original Danish edition published by Wilhelm Hansen, in Copenhagen, 1931).

Melin, William Eugene. “The Music of Johannes Tinctoris: A Comparative Study of Theory and Practice.” PhD diss., Ohio State University, 1973.

Milsom, John. “‘Imitatio,’ ‘intertextuality’, and early music.” In Citation and authority in Medieval and Renaissance musical culture: Learning from the learned, edited by Suzannah Clark and Elizabeth Eva Leach, 141–51. Woodbridge: Boydell & Brewer, 2005.

Moll, Kevin. Counterpoint and Compositional Process in the Time of Dufay: Perspectives from German Musicology. Edited and translated by Kevin Moll. New York: Garland Publishing Inc., 1997.

Morgan, Alexander. "[Renaissance Interval-Succession Theory: Treatises and Analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)". PhD diss., McGill University, 2017.

Morris, R. O. Contrapuntal Technique. Oxford: Oxford University Press, 1922.

Pontio, Pietro. Ragionamento di musica. Compiled by Suzanne Clercx. Kassel: Bärenreiter, 1959. Originally published Parma: 1588.

———. [Ragionamento di musica](http://www.ums3323.paris-sorbonne.fr/TREMIR/TReMiR_Pontio/R0_start.htm). Electronic version published by Dupraz, Christophe. Traités Musicaux Romans, 2013. Accessed August 14, 2016.

Rothfarb, Lee. “Tinctoris vs. Tinctoris: Theory and Practice of Dissonance in Counterpoint.” In Theory Only 9.2–3 (1986): 3–31.

Sachs, Klaus-Jürgen. "[Counterpoint](http://www.oxfordmusiconline.com/subscriber/article/grove/music/06690)."  Grove Music Online. (accessed July 12, 2016).

———. Der Contrapunctus im 14. und 15. Jahrhundert: Untersuchungen zum Terminus, zur Lehre und zu den Quellen. Wiesbaden: Steiner, 1974.

Schubert, Peter. Modal Counterpoint, Renaissance Style, 2nd ed. New York: Oxford University Press, 2008.

Schubert, Peter and Julie Cumming, “Another Lesson from Lassus: using Computers to Analyze Counterpoint.” Early Music 43.4 (November 2015): 577–86.

Siegler, Andie, and Jon Wild. “Schematizing the Treatment of Dissonance in 16th-century Counterpoint.” In Proceedings of the International Society for Music Information Retrieval (2015): 645–650.

Tinctoris, Johannes. Liber de arte contrapuncti. In Johannes Tinctoris Opera Theoretica. Compiled by Albert Seay. n.p.: American Institute of Musicology, 1975. Originally written 1477.

———. Liber de arte contrapuncti. Translated by Albert Seay. Rome: American Institute of Musicology, 1961. Originally written c. 1477.

———. "[Liber de arte contrapuncti](http://earlymusictheory.org/Tinctoris/texts/deartecontrapuncti/). Translated by Jeffrey Dean. Last accessed November 16, 2015. Originally written 1477.

Trachier, Olivier. Contrepoint du XVIe siècle. Paris: Durand, 1999.

Vicentino, Nicola. Ancient music adapted to modern practice (L’antica musica ridotta alla moderna prattica). Translated by Maria Rika Maniates and edited by Claude Palisca. New Haven, Yale University Press 1996. Originally published 1555.

Zarlino, Gioseffo. Art of Counterpoint. Translated by Guy Marco and Claude Palisca, edited by Claude Palisca. New Haven and London: Yale University Press, 1968. Originally published: 1558.