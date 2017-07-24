---
title: dissonant filter
author: ["Alexander Morgan", "Craig Sapp"]
creation_date: 29 May 2017
last_updated: 10 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
examplewidth: 1200
vim: ft=html
verovio: "true"
keywords: "interface commands"
summary: "The dissonant filter labels non-harmonic tones in contrapuntal textures."
permalink: /filters/dissonant/index.html
---

The dissonant filter automatically labels the function of non-harmonic
notes in contrapuntal textures.  All harmonic seconds and sevenths are considered
dissonant as well as fourths above the lowest sounding voice.

Each input `**kern` spine is
expected to be monophonic and have no subspine branching.  If there
are chords in the music, only the first note of the chord is used, and
secondary subspines will be ignored.

Below is an example of the dissonant filter in action using an
excerpt from Josquin's chanson <a href="http://josquin.stanford.edu/work/?id=Jos2705">Ce povre mendiant/Pauper sum ego</a>.  To
apply the filter to a file, include the line `!!!filter: dissonant`
anywhere in the file.  The dissonant function labels for each voice
will be inserted in spines immediately to the right of each `**kern`
spine.  In the following display the labels are shown above the
notes to which they apply.  `P` means a rising passing tone and `p`
means a lower passing tone.  See the complete list of label
abbreviations further below.

{% include verovio.html
	source="josex"
	scale="40"
	spacingStaff="4"
	spacingSystem="4"
	pageWidth="1450"
	tabsize="10"
%}

<script type="application/x-humdrum" id="josex">!!!filter: dissonant
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

Try editing the above Humdrum score to generate various types of
dissonances.  Removing the first line (`!!!filter: dissonant`) will
turn of the dissonance analysis, and adding `-u` to
`!!!filter: dissonant -u` will merge subcategories into a single
main category for the dissonant types.



## Dissonant function labels ##

Dissonant notes are marked with single-letter label abbreviations
in the notation as well as in the Humdrum score.  The first table
below gives the detailed default label categories used in the
dissonance analysis, while the second table gives more generalized
categories that do not distinguish melodic directions.

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
<tr><td> D </td><td> double neighbor upper then lower</td>      <td> d </td>  <td> double neighbor lower then upper</td>        </tr>
<tr><td> E </td><td> upper &eacute;chapp&eacute;e</td>          <td> e </td>  <td> lower &eacute;chapp&eacute;e</td>            </tr>
<tr><td> C </td><td> ascending short nota cambiata</td>         <td> c </td>  <td> descending short nota cambiata</td>          </tr>
<tr><td> K </td><td> ascending long nota cambiata</td>          <td> k </td>  <td> descending long nota cambiata</td>           </tr>
<tr><td> A </td><td> rising anticipation</td>                   <td> a </td>  <td> descending anticipation</td>                 </tr>
<tr><td> I </td><td> reverse ascending nota cambiata</td>       <td> i </td>  <td> reverse descending nota cambiata</td>        </tr>
<tr><td> J </td><td> reverse upper &eacute;chapp&eacute;e</td>  <td> j </td>  <td> reverse lower &eacute;chapp&eacute;e</td>    </tr>
<tr><td> S </td><td> ternary suspension</td>                    <td> s </td>  <td> binary suspension</td>                       </tr>
<tr><td> G </td><td> ternary suspension agent</td>              <td> g </td>  <td> binary suspension agent</td>                 </tr>
<tr><td> F </td><td> fake susp. approached by step up</td>      <td> f </td>  <td> fake susp. approached by step down</td>      </tr>
<tr><td> x </td><td> resolution against suspension dissonance</td><td> r </td>  <td> suspension repeated note</td>              </tr>
<tr><td> M </td><td> suspension missing agent approached by step up </td> <td> m </td>  <td> suspension missing agent approached by step down </td> </tr>
<tr><td> Q </td><td> dissonant 3rd quarter rising passint tone</td>  <td> q </td>  <td> dissonant 3rd quarter falling passing tone</td>      </tr>
<tr><td> B </td><td> dissonant 3rd quarter upper neighbor</td>  <td> b </td>  <td> dissonant 3rd quarter lower neighbor</td>    </tr>
<tr><td> T </td><td> appoggiatura approached from below</td>    <td> t </td>  <td> appoggiatura approached from above</td>      </tr>
<tr><td> V </td><td> ascending accented passing tone</td>       <td> v </td>  <td> descending accented passing tone</td>        </tr>
<tr><td> W </td><td> accented upper neighbor</td>               <td> w </td>  <td> accented lower neighbor</td>                 </tr>
<tr><td>   </td><td> (no ascending form of chanson idiom)</td>  <td> h </td>  <td> chanson idiom</td>                       </tr>
<tr><td> Z </td><td> unclassified dissonance, 2nd or 7th interval</td> <td> z </td ><td> unclassified dissonance, 4th interval</td></tr>
</table>

The `-u` option (meaning *undifferentiated*) collapses up/down
subcategorizations into a single label designated by an uppercase
letter:

<table class="dense twocol">
<tr><th>Label</th><th> Meaning</th>                             <th>Label</th><th> Meaning</th>                                 </tr>
<tr><td> P </td><td> passing tone</td>                          <td> F </td><td> fake suspension</td></tr>
<tr><td> N </td><td> neighbor tone</td>                         <td> D </td><td> double neighbor</td></tr>
<tr><td> E </td><td> &eacute;chapp&eacute;e</td>                <td> R </td><td> suspension repeated note</td></tr>
<tr><td> C </td><td> short nota cambiata</td>                   <td> M </td><td> supension missing agent</td></tr>
<tr><td> K </td><td> long nota cambiata</td>                    <td> Q </td><td> dissonant third quarter passing tone</td></tr>
<tr><td> A </td><td> anticipation</td>                          <td> B </td><td> dissonant 3rd quarter neighbor</td></tr>
<tr><td> T </td><td> appoggiatura</td>                          <td> V </td><td> accented passing tone</td></tr>
<tr><td> I </td><td> incomplete anterior neighbor</td>          <td> W </td><td> accented neighbor tone</td></tr>
<tr><td> J </td><td> incomplete posterior neighbor</td>         <td> H </td><td> chanson idiom</td></tr>
<tr><td> S </td><td> suspension</td>                            <td> X </td><td> resolution against suspension dissonance</td></tr>
<tr><td> G </td><td> suspension agent</td>                      <td> Z </td><td> unclassified dissonance</td></tr>
</table>

Examples of each dissonant type are given below.  Note that the
musical examples are [generated dynamically using verovio](/myvhv/static)
within the page, and the *dissonant* tool labels notes as the
webpage is loaded.



### Passing notes (P, p) ###

A passing tone is approached by step and left by step in the
same direction. The preceding note must be metrically stronger than
the dissonant note, and the note the passing tone is dissonant
against must begin before the passing tone and must sustain at least
through the end of the passing tone. These are labeled with uppercase
`P` and lowercase `p` for ascending and descending passing tones
respectively.

{% include verovio.html
	humdrum-visible="false"
	source="passing"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="passing">**kern	**kern
*M2/4	*M2/4
4C	8cL
.	8dJ
4AA	4e
=2	=2
4FF	8fL
.	8eJ
4GG	4d
=	=
*-	*-
!!!filter: dissonant
</script>



### Neighbor notes (N, n) ###

Neighbor tones have similar requirements as passing tones, except 
instead of being approached and left by step in the same direction,
neighbor tones are approached and left by step in opposite directions.
`N` and `n` are used to label upper and lower neighbors respectively.

{% include verovio.html
	humdrum-visible="false"
	source="nei"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="nei">**kern	**kern
*M2/4	*M2/4
4C	8ccL
.	8ddJ
4AA	4cc
=2	=2
4GG	8bL
.	8aJ
4EE	4b
=	=
*-	*-
!!!filter: dissonant
</script>



### Double neighbors (D, d) ###

In a double neighbor figure, a primary note is ornamented by both an upper and lower neighbor before returning to the primary note. Both dissonant notes are given the same label based on which type of dissonant neighbor comes first, `D` if the figure begins with an upper neighbor, and `d` if it begins with a lower neighbor. While the first dissonance must be relatively weak metrically compared to the primary note, the second of the two double neighbors can be accented, such as in this excerpt from the chanson attributed to Josquin [Mala se nea](http://josquin.stanford.edu/work/?id=Jos2915).

{% include verovio.html
	humdrum-visible="false"
	source="dbln"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="dbln">**kern	**kern
*Ivox	*Ivox
*I"Bassus	*I"Superius
*I'B	*I'S
*clefF4	*clefG2
*k[b-]	*k[b-]
*M2/1	*M2/1
*met(C|)	*met(C|)
=50	=50
1C	2g/
.	.
.	2g/
.	.
[1FF	2a/
.	2b-\
=51	=51
0FF]	2.cc\
.	.
.	4b-\
.	4a/
.	4g/
.	4b-\
.	4a/
=52	=52
2BB-/	0b-
4BB-/	.
4BB-/	.
2BB-/	.
.	.
2BB-/	.
==	==
*_	*_
!!!filter: dissonant
</script>



###  &Eacute;chapp&eacute;e notes (E, e) ###

An &eacute;chapp&eacute;e (also called an *escape tone*) is approached
by step and left by leap in the opposite direction. The dissonant
note must be metrically weaker than the note that precedes it and
a note in another voice must start before the &Eacute;chapp&eacute;e
and sustain at least until the end of the &Eacute;chapp&eacute;e.

{% include verovio.html
	humdrum-visible="false"
	source="chap"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="chap">**kern	**kern
*clefF4	*clefG2
*M2/4	*M2/4
4F	8aL
.	8gJ
4E	4cc
=2	=2
4F	8aL
.	8bJ
4G	4g
=	=
*-	*-
!!!filter: dissonant
</script>



###  Cambiatas notes (C, c, K, k) ###

A *nota cambiata* is approaced by step and left by a leap of a third
in the same direction. It must be metrically weaker than the note
that preceded it. If after leaping a third, the melody moves a step
in the opposite direction (thus filling in the note that was skipped
over) the dissonance gets a `K` or `k` label for the long-form
cambiata. If this change of direction does not occur then a `C` or
`c` label is used. 

{% include verovio.html
	humdrum-visible="false"
	source="camb_dn"
	scale="50"
	pageWidth="1400"
	tabsize="10"
	spacingLinear="0.15"
	spacingNonLinear="0.50"
%}
<script type="application/x-humdrum" id="camb_dn">**kern	**kern
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
=	=
*-	*-
!!!filter: dissonant
</script>

As with most other dissonance labels (with the
exception of suspension and agent labels), a lowercase letter means
it was approached by step down, as in the example above, and an
uppercase letter means the dissonance was approached by step up,
as in the example below.

{% include verovio.html
	humdrum-visible="false"
	source="camb_up"
	scale="50"
	pageWidth="1300"
	tabsize="10"
	spacingLinear="0.10"
	spacingNonLinear="0.45"
%}
<script type="application/x-humdrum" id="camb_up">**kern	**kern
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
=	=
*-	*-
!!!filter: dissonant
</script>



###  Anticipations (A, a) ###

As demonstrated in the example below, anticipations that are
approached by a step up are labeled with `A`; otherwise, they are
labeled with `a` when approached by a step down, and then repeated
in place. An anticipation is metrically weaker than the notes before
and after it.

{% include verovio.html
	humdrum-visible="false"
	source="ant"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="ant">**kern	**kern
*clefG2	*clefG2
*M4/2	*M4/2
4g	2ee
4f	.
1f	4dd
.	4cc
.	4dd
.	4ee
2e	2ee
=	=
*-	*-
!!!filter: dissonant
</script>



###  Reverse nota cambiatas (I, i) ###

A "reverse" nota cambiata is a weak dissonance approached by leap and resolved down by step in the same direction.  It is labeled with an `I` or an `i` for its ascending and descending versions respectively. These are relatively rare in the Renaissance. This example from the Gloria Ockeghem's [Missa Fors seulement](http://josquin.stanford.edu/work/?id=Ock1007) includes an incomplete anterior lower neighbor, labeled with an `i`.

{% include verovio.html
	humdrum-visible="false"
	source="rnc"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="rnc">**kern	**kern
*clefF4	*clefGv2
*k[]	*k[]
*M3/1	*M3/1
*met(O)	*met(O)
=8-	=8-
2.D\	1A
4BB/	.
1AA	1A
.	.
1F	1A
.	.
.	.
=	=
*-	*-
!!!filter: dissonant
</script>



###  Reverse &eacute;chapp&eacute;es (J, j) ###

The "reverse" &eacute;chapp&eacute;e is a weak dissonance that is approached by leap and then resolved by step in the opposite direction. It is labeled `J` when that initial leap is up, and `j` when it is down, similar to neighbor tones. This often occurs as an ornament of a suspension. While only dissonant suspensions are labeled, consonant suspensions also receive this same type of ornamentation. The example below taken from the Sanctus of the [Missa Sub tuum presidium](http://josquin.stanford.edu/work/?id=Jos0405) contains two parallel reverse &eacute;chapp&eacute;es, one decorating a consonant suspension in the Altus, and the other ornamenting a consonant suspension (unlabeled) in the Superius.

{% include verovio.html
	humdrum-visible="false"
	source="reve"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="reve">**kern	**kern	**kern	**kern
*I"Bassus	*I"Tenor	*I"Altus	*I"Superius
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=166	=166	=166	=166
1AA	1A	2c\	2r
.	.	2.A/	2.cc\
1r	1E	.	.
.	.	4F/	4a/
.	.	2G/	4b\
.	.	.	4e/
1r	2r	1A	2e/
.	[2c\	.	[2a/
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



###  Suspensions (S, s, G, g) ###

A suspension consists of a voice that becomes dissonant either by
sustaining or restriking a note before resolving the dissonance
down by step. This sustained voice was referred to as the *patient*
by Artusi, and it gets an `S` or `s` label at the moment of the
dissonance. Another voice strikes a note that is dissonant against
the suspended note, and this voice gets a `G` or `g` label for
*agent*. It is common to have more than one agent per suspension
such as in m.&nbsp;37 in the example below.

{% include verovio.html
	humdrum-visible="false"
	source="sus"
	scale="40"
	spacingLinear="0.05"
	spacingNonLinear="0.30"
	pageWidth="1500"
	tabsize="10"
	url="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Obr2018"
%}
<script type="application/x-humdrum" id="sus">**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=34-	=34-	=34-	=34-
1AA	0.r	1e	2c/
.	.	.	2cc\
2BB/	.	2d\	2b\
2C/	.	2c\	1a
2D\	.	1B	.
2E\	.	.	2g#i/
=35	=35	=35	=35
1AA	0.E	1A	1a
1r	.	1B	1g
1AA	.	[1c	2a/
.	.	.	4g/
.	.	.	4f/
=36	=36	=36	=36
1C	1E	1c]	1e
1D	1F	1A	1d
1GG	[1G	1B	2e/
.	.	.	[2g/
=37	=37	=37	=37
1C	1G]	1c	2g/]
.	.	.	1e
0D	0F	0A	.
.	.	.	4d/
.	.	.	4c/
.	.	.	1d
=38	=38	=38	=38
2GG/	0.E	2B\	1e
2.AA/	.	2.c\	.
.	.	.	2r
4GG/	.	4B\	.
2.C/	.	2.e\	1g
4BB/	.	4d\	.
2GG/	.	2B\	2e/
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>

This example, taken from Obrecht's motet [Mille
quingentis](http://josquin.stanford.edu/work/?id=Obr2018), features
both a binary and a ternary suspension. The first suspension
(in m.&nbsp;34) is binary, because the dissonance phase of the suspension
lasts a unit of time (in this case a minim, or half note) that groups in twos in
the given mensuration. The second suspension above (in m.&nbsp;37), its
dissonant phase lasts a semibreve, or whole note, (when ornamentation is disregarded)
so this suspension is ternary and receives uppercase `S` and `G`
labels. If you prefer not to distinguish between binary and ternary
suspensions, use the `-u` option and all
suspensions and agents will be labeled with uppercase letters.

Consonant suspensions are ignored by the dissonant tool.



### Rearticulated suspension (r) ###

The most common type of suspension ornamentation in the Renaissance is to leap down a third from the suspened dissonance before resolving both dissonances with a step up. This type of ornament falls under the larger category of reverse &eacute;chapp&eacute;es (see above). Another type of ornamentation consists of a simple rearticulation
of the suspended note before it resolves down by step. The reartuclated
note is generally a semi-minim (quarter note) and is labeled in the
analyses with an `r`. While this figuration (shown below) does occur
in tonal music, there are almost no occurrences of this in the
entire [JRP](http://josquin.stanford.edu) database of scores. This
demonstrates how dissonance analysis can be used to inform the study
of style change over time.

{% include verovio.html
	humdrum-visible="false"
	source="rsus"
	scale="50"
	spacingLinear="0.1"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="rsus">**kern	**kern
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
=	=
*-	*-
!!!filter: dissonant
</script>



###  Fake Suspensions (F, f) ###

Sometimes the preparation of a suspension is itself dissonant like
in the example below from the Kyrie in Mouton's 
[Missa Da pacem](http://josquin.stanford.edu/work/?id=Mou1020a).
This is often referred to as a *fake suspension* though would
more accurately be called a fake preparation to an otherwise normal suspension. It is usually approached by
step up or down and remains in place or is restruck to become the
dissonant portion of a suspension. Since we know the suspension
will resolve down by step, we use an uppercase `F` or
lowercase `f` to convey whether the dissonance was approached by
leap or by step respectfully. Because this happens over a pedal,
and an agent is also needed for the suspension, this is generally
only found in three or more voices, though could happen in two voices
if the pedal tone were rearticulated at the moment it serves as the
agent of the suspension.

{% include verovio.html
	humdrum-visible="false"
	source="fsus"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="fsus">**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1
=26	=26	=26	=26
2D	0A	4d]	2f
.	.	4c	.
2C	.	2e-i	1g
1D	.	[1d	.
.	.	.	2f#i
=27	=27	=27	=27
1GG	0G	2d]	0g
.	.	2.B-	.
1r	.	.	.
.	.	4c	.
.	.	2d	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>

Occasionally a fake suspension is preceded by an anticipation and these are detected as well, such as
in the example below taken from the same Mouton Kyrie.

{% include verovio.html
	humdrum-visible="false"
	source="afsus"
	scale="50"
	spacingLinear="0.35"
	spacingNonLinear="0.7"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="afsus">**kern	**kern	**kern	**kern
*I'B	*I'T	*I'A	*I'S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M3/1	*M3/1	*M3/1	*M3/1
=9	=9	=9	=9
1C	0.c	1r	4a
.	.	.	4b-
.	.	.	2.cc
1E	.	1g	.
.	.	.	4b-
.	.	.	1b-
1F	.	2.f	.
.	.	.	2a
.	.	4e	.
=10	=10	=10	=10
2.G	0B-	4d	1b-
.	.	4c	.
.	.	2B-	.
4F	.	.	.
2D	.	2F	2r
2.E-i	.	2G	2.g
.	1r	1B-	.
4D	.	.	4f
2BB-	.	.	2d
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant

</script>

Occasionally a fake suspension is preceded by an anticipation as
in the example above taken from the same Mouton Kyrie. In this case
the fake suspension label takes the same case as that of the
anticipation.



###  Suspensions with missing agents (M, m) ###

In some cases a suspension seems to be missing an attacked agent.
This figure consists of a voice moving up or down by step, then
sustaining over the following beat, and then resolving down by step
all over a pedal tone. This dissonance is labeled `M` or `m` based
on whether the dissonant note is approached by leap or by step
respectively. The example below is taken from Obrecht's motet [Factor
Orbis](http://josquin.stanford.edu/work/?id=Obr2010).

{% include verovio.html
	humdrum-visible="false"
	source="msus"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="msus">**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M3/1	*M3/1	*M3/1	*M3/1
*met(O)	*met(O)	*met(O)	*met(O)
=59-	=59-	=59-	=59-
1F	1A	1d	2a/]
.	.	.	4g/
.	.	.	4f/
0E	0B	0e	2g/
.	.	.	1a
.	.	.	2g#i/
=60	=60	=60	=60
1AA	1A	1e	1a
2r	2r	2r	1r
2AA/	2A/	2e\	.
2AA/	2A/	2e\	1r
2AA/	2A/	2e\	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Chanson idiom (h) ###

A chanson idiom functions as an ornamented anticipation to the agent
of a suspension and is labeled with an `h`. It usually occurs in
the placement of a weak minim, (half-note) and consists of a quarter
note that is dissonant against the preparation to the suspension
and is approached by step down.  This dissonance is also left by
step down to another quarter note that is then followed by the agent
of the suspension a step up (on the same pitch as the chanson idiom).
The example below is taken from the contra and tenor parts of the
chanson [Cela sans plus](http://josquin.stanford.edu/work/?id=Jos2704)
attributed to Josquin des Prez:

{% include verovio.html
	humdrum-visible="false"
	source="chi"
	url="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2704"
	scale="50"
	linearSpacing="0.1"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="chi">**kern	**kern
*clefG2	*clefG2
*clefGv2	*clefGv2
*k[]	*k[]
*M2/1	*M2/1
*met(C|)	*met(C|)
=35-	=35-
2d\	2B\
1g	4A/
.	4G/
.	1A
2f#i\	.
=36	=36
1g	1G
1f	2r
.	[2d\
=	=
*-	*-
!!!filter: dissonant
</script>



### Dissonant 3rd quarter passing tone (Q, q) ###

A dissonant third quarter passing tone, a regular passing tone. It
corresponds to a dissonance in the metric position of a weak minim
that lasts only a quarter note. It is approached and left by step
in the same direction and must be preceded by a note with a duration
of at least a minim (half-note). If it descends, it gets the `q`
label as in the following example.

A dissonant third quarter passing tone, labeled `q` in the example
below, is similar to a descending passing tone. It corresponds to
a dissonance in the metric position of a weak minim that lasts only
a quarter note. It is approached and left by a step down and must
be preceded by a note with a duration of at least a minim (half
note).  There is no ascending form for this dissonance type.

{% include verovio.html
	humdrum-visible="false"
	source="d3qpd"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qpd">**kern	**kern
*clefG2	*clefG2
*M2/1	*M2/1
2f	1.a
2e	.
1d	.
.	4g
.	4f
=	=
*-	*-
!!!filter: dissonant
</script>

Though it is less common, when the same figure happens in its
ascending form, it gets labeled with a `Q` as in the following
example taken from the Superius and the Altus of the Credo in
Josquin's [Missa De beata
virgine](http://josquin.stanford.edu/work/?id=Jos0303c).

{% include verovio.html
	humdrum-visible="false"
	source="d3qpu"
	scale="50"
	spacingLinear="1.75"
	spacingNonLinear="0.8"
	pageWidth="1400"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qpu">**kern	**kern
*clefGv2	*clefG2
*k[]	*k[]
*M2/1	*M2/1
*met(C|)	*met(C|)
=113-	=113-
1r	1.g
1G	.
.	4a/
.	4b\
=114	=114
1E	1cc
[1A	1cc
=	=
*-	*-
!!!filter: dissonant
</script>



### Dissonant third quarter neighbor (B, b) ###

This dissonance is the neighbor-tone version of the dissonant third
quarter passing tone. The example below is taken from the altus and
bassus parts from the Credo of Josquin's [Missa La belle se
siet](http://josquin.stanford.edu/work/?id=Jos1303c) (NJE&nbsp;13.3).

The dissonance type consists of a neighbor tone in the metric
position of a weak minim (half-note) that lasts only a quarter note
in duration. Although we detect both upper- and lower-neighbor
varieties of this dissonance type, like regular neighbor tones, the
dissonant third quarter lower neighbor is by far more common than
the upper-neighbor version. The upper- and lower-neighbor versions
of this dissonance type are labeled with a `B` and a `b` repsectfully.

{% include verovio.html
	humdrum-visible="false"
	source="d3qn"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="d3qn">**kern	**kern
*I'B	*I'A
*clefF4	*clefGv2
*k[b-]	*k[b-]
*M3/1	*M3/1
*met(C|3)	*met(C|3)
=183-	=183-
1C	1G
1C	1.G
1C	.
.	4F
.	4G
=	=
*-	*-
!!!filter: dissonant
</script>



### Appoggiaturas (T, t) ###

An appoggiatura is a dissonance that is relatively accented with respect to the notes before and after it. It is approached by leap and resolved down by step. It is labeled with a `T` when the leap is up and `t` when the leap is down.

{% include verovio.html
	humdrum-visible="false"
	source="appgg"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="appgg">**kern	**kern
*I'B	*I'A
*clefF4	*clefGv2
*k[b-]	*k[b-]
*M3/1	*M3/1
*met(C|3)	*met(C|3)
=183-	=183-
1C	1G
1C	1.G
1C	.
.	4F
.	4G
=	=
*-	*-
!!!filter: dissonant
</script>



### Accented passing tones (V, v) ###

Accented passing tones are metrically strong with respect to the notes before and after them, and last no longer than the following note. They are approached and left by step in the same direction and labeled `V` when those steps are up, and `v` when those steps are down. They will get detected even if they are decorated with an anticipation immediately before. This dissonance definition could correspond to dissonant third quarter passing tones, and also the chanson idiom dissonance type. An accented passing tone will only get labeled as such if it does not meet the stricter requirements for any other dissonance type. In the Gloria of [Missa Cum iocunditate](http://josquin.stanford.edu/work/?id=Jos0304) attributed to Josquin, accented passing tones are found in certain contrapuntal dispositions where a primary motive is set against itself in multiple voices, such as in the excerpt below.

{% include verovio.html
	humdrum-visible="false"
	source="accp"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="accp">**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*Ivox	*Ivox	*Ivox	*Ivox
*I"Bassus	*I"Tenor	*I"Altus	*I"Superius
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=138	=138	=138	=138
2r	0r	0A	2c/
1D	.	.	2.A/
.	.	.	4B/
2D\	.	.	4c/
.	.	.	4d/
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Accented neighbor tones (W, w) ###

Accented neighbor tones are metrically strong with respect to the notes before and after them, and last no longer than the following note. They are approached and left by step in opposite directions and labeled `W` when approached by step up, and `w` when approached by step down. They will get detected even if they are decorated with an anticipation immediately before. This dissonance definition also matches that of dissonant third quarter neighbor tones, and potentially the `L` and `Y` types. An accented neighbor tone will only get labeled as such if it does not meet the stricter requirements for any other dissonance type. The excerpt below taken from the motet [Benedicite, omnia opera](http://josquin.stanford.edu/work/?id=Jos1402) attributed to Josquin contains an accented upper neighbor in the Altus.

{% include verovio.html
	humdrum-visible="false"
	source="accn"
	scale="35"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="accn">**kern	**kern	**kern	**kern
*I"B	*I"T	*I"A	*I"S
*clefF4	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)
=78	=78	=78	=78
1G	2d\	2r	2b-\
.	2d\	1g	2b-\
1C	[1c	.	[1cc
.	.	2e\	.
=79	=79	=79	=79
2r	1c]	2f\	1cc]
1c	.	2e\	.
.	2r	1c	1r
2A\	[2c\	.	.
=	=	=	=
*-	*-	*-	*-
!!!filter: dissonant
</script>



### Resolution against suspension dissonance (X, x) ###

When a voice sounds the note of resolution of a suspension in a descending line against the dissonant portion of the suspension in another voice, it is labeled with an `x`. There is no ascending form of this dissonance so an uppercase `X` is only used if the -u setting is invoked. This dissonance necessarily only occurs when three or more voices are present, because in addition to the dissonance itself, two other voices must form a suspension. It often occurs in even thicker textures though, such the excerpt below taken from the motet [Victime paschali laudes](http://josquin.stanford.edu/work/?id=Jos2207) by Brunet.

{% include verovio.html
	humdrum-visible="false"
	source="resx"
	scale="35"
	pageWidth="1150"
	tabsize="10"
%}
<script type="application/x-humdrum" id="resx">**kern	**kern	**kern	**kern	**kern	**kern
*staff6	*staff5	*staff4	*staff3	*staff2	*staff1
*Ivox	*Ivox	*Ivox	*Ivox	*Ivox	*Ivox
*I'B2	*I'B1	*I'T	*I'A2	*I'A1	*I'S
*clefF4	*clefF4	*clefGv2	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)
=189	=189	=189	=189	=189	=189
2G\	1E	4d\]	2g\	2B-\	4a/]
.	.	4B-\	.	.	4g/
2C/	.	2c\	2e\	2G/	1g
2.F\	1D	1d	4f\	1A	.
.	.	.	4e\	.	.
.	.	.	4d\	.	2f#i/
4E\	.	.	4c\	.	.
=190	=190	=190	=190	=190	=190
2D\	2GG/	0d	1B-	[0Gl	[0gl
2.G\	1G	.	.	.	.
.	.	.	2r	.	.
4F\	.	.	.	.	.
4E-i\	2F\	.	2B-\	.	.
4D\	.	.	.	.	.
*-	*-	*-	*-	*-	*-
!!!filter: dissonant</script>



### Parallel accompaniment (L, l) ###

If a dissonance does not correspond to any identifiable categories
(and would normally receive a `Z` label), and moves in parallel
motion by another voice that is an idenfiable dissonance, this
parallel accompaniment is given an `L` if it is approached by step
up, or an `l` if it is approached by step down. This type of
dissonance often occurs in tandem with a chanson idiom such as in
the example below taken from Lannoy's [Cela sans
plus](http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2704).
While the voices are still analyzed in a pairwise fashion, since
this dissonance type requires a second voice to be in an identifiable
dissonance condition with a third voice, this type is only identified
in pieces with three or more voices.

{% include verovio.html
	humdrum-visible="false"
	source="para"
	scale="50"
	pageWidth="1300"
	tabsize="10"
%}
<script type="application/x-humdrum" id="para">**kern	**kern	**kern
*clefGv2	*clefGv2	*clefG2
*k[]	*k[]	*k[]
*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)
=20-	=20-	=20-
1G	1.g	2ee
.	.	2.dd
1B	.	.
.	.	4cc
.	2f	4b
.	.	4a
=21	=21	=21
2c	2e	2g
4B	4d	1cc
4A	4c	.
1G	1d	.
.	.	2b
=22	=22	=22
1r	0c	0cc
1g	.	.
=	=	=
*-	*-	*-
!!!filter: dissonant</script>


### Only against known dissonance (Y, y) ###

When a note is only dissonant against known dissonance types, it
receives a `Y` or `y` label depending on whether it was approached
from below or from above respectively. This sort of scenario often
occurs in thicker textures, such as in the example below with both
a `Y` and a `y` taken from the Sanctus of the [Missa Pro
defunctus](http://josquin.stanford.edu/work/?id=Jos0404) attributed
to Josquin.

{% include verovio.html
	humdrum-visible="false"
	source="only"
	scale="50"
	pageWidth="1000"
	tabsize="10"
%}
<script type="application/x-humdrum" id="only">**kern	**kern	**kern	**kern	**kern	**kern
*clefF4	*clefGv2	*clefGv2	*clefGv2	*clefGv2	*clefG2
*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]	*k[b-]
*M2/1	*M2/1	*M2/1	*M2/1	*M2/1	*M2/1
*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)	*met(C|)
=29-	=29-	=29-	=29-	=29-	=29-
1D	0F	1.d	4A	1A	2f
.	.	.	4G	.	.
.	.	.	4F	.	4g
.	.	.	4E	.	4a
1BB-	.	.	1D	1r	1b-
.	.	2d	.	.	.
=	=	=	=	=	=
*-	*-	*-	*-	*-	*-
!!!filter: dissonant</script>


### Unknown dissonances (Z, z) ###

Dissonances not assignable to one of the above categories are given
a `Z` label to indicate their function is unknown.  A capital `Z`
means that the interval of the dissonance is a 2nd or 7th.  A
lower-case `z` means that the dissonance is a 4th against the lowest
sounding note in the sonority.

## URL filtering of repertories ##

The dissonant tool can be used with available VHV repertories by adding the
filter to the URL for the works, such as with the Tasso in Music Project:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=dissonant)

To remove lyric text from analysis results, use the filter: `extract -i kern | dissonant`:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant](http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant)

The filter `extract -i kern` extracts only `**kern` spines and filters out non-kern spines.


{% include image.html
	file="textless.png"
	alt="removing lyric text before displaying analysis."
	max-width="90%"
	url="http://verovio.humdrum.org/?k=ey&file=tmp&filter=extract%20-ikern%7cdissonant"
	caption="<i>Dissonant</i> analysis after removing lyric text (click for live demo)."
%}

## JRP dissonant tool ##

<style>

.jrp-button {
	background: #c86843;
	color: white;
	font-size: 90%;
	display: inline-block;
	border: none;
	text-align: center;
	padding: 1px 3px;
}

</style>

Work pages on the Josquin Research Project website have links 
for the given work to view the dissonant labeling analysis in VHV.
For example the page:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[http://josquin.stanford.edu/work/?id=Jos2801](http://josquin.stanford.edu/work/?id=Jos2801)

contains a button labeled <span class="jrp-button">Dissonant</span> on the bottom left side of the page.  Clicking on that button will load
the score for the current page into VHV and do an online analysis of the dissonant labels:


{% include image.html
	file="jrp-dissonant.png"
	alt="dissonant button on JRP workpage."
	max-width="60%"
	url="http://josquin.stanford.edu/work/?id=Jos2801"
	caption="<i>Dissonant</i> analysis button on JRP work pages."
%}

### Dissonance summaries ###

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

DeFord, Ruth. Tactus Mensuration, and Rhythm in Renaissance Music. Cambridge: Cambridge University Press, 2015.

Fuller, Sarah. “Contrapunctus Theory, Dissonance Regulation, and French Polyphony of the Fourteenth Century.” In Medieval Music in Practice: Studies in Honor of Richard Crocker, edited by Judith Peraino, 113–52. Middleton, Wisconsin: American Institute of Musicology, 2013.

———. “Organum – discantus – contrapunctus in the Middle Ages.” In The Cambridge History of Western Music Theory, edited by Thomas Christensen, 477–502. Cambridge: Cambridge University Press, 2002.

Jeppesen, Knud. Counterpoint: The Polyphonic Vocal Style of the Sixteenth Century. Translated by Glen Haydon. New York: Dover Publications, 1992 (original Danish edition published by Wilhelm Hansen, in Copenhagen, 1931).

Melin, William Eugene. “The Music of Johannes Tinctoris: A Comparative Study of Theory and Practice.” PhD diss., Ohio State University, 1973.

Moll, Kevin. Counterpoint and Compositional Process in the Time of Dufay: Perspectives from German Musicology. Edited and translated by Kevin Moll. New York: Garland Publishing Inc., 1997.

Morgan, Alexander. "[Renaissance Interval-Succession Theory: Treatises and Analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)." PhD diss., McGill University, 2017.

Morris, R. O. Contrapuntal Technique. Oxford: Oxford University Press, 1922.

Patrick, P. H. & Strickler, K. (1978) "A Computer-Assisted Study of Dissonance in the Masses of Josquin Desprez." Computers and the Humanities. 12 (4), 341&ndash;364.

Pontio, Pietro. Ragionamento di musica. Compiled by Suzanne Clercx. Kassel: Bärenreiter, 1959. Originally published Parma: 1588.

———. [Ragionamento di musica](http://www.ums3323.paris-sorbonne.fr/TREMIR/TReMiR_Pontio/R0_start.htm). Electronic version published by Dupraz, Christophe. Traités Musicaux Romans, 2013. Accessed August 14, 2016.

Rothfarb, Lee. “Tinctoris vs. Tinctoris: Theory and Practice of Dissonance in Counterpoint.” In Theory Only 9.2–3 (1986): 3–31.

Sachs, Klaus-Jürgen. "[Counterpoint](http://www.oxfordmusiconline.com/subscriber/article/grove/music/06690)."  Grove Music Online. (accessed July 12, 2016).

———. Der Contrapunctus im 14. und 15. Jahrhundert: Untersuchungen zum Terminus, zur Lehre und zu den Quellen. Wiesbaden: Steiner, 1974.

Schubert, Peter. Modal Counterpoint, Renaissance Style, 2nd ed. New York: Oxford University Press, 2008.

Siegler, Andie, and Jon Wild. “Schematizing the Treatment of Dissonance in 16th-century Counterpoint.” In Proceedings of the International Society for Music Information Retrieval (2015): 645–650.

Tinctoris, Johannes. Liber de arte contrapuncti. In Johannes Tinctoris Opera Theoretica. Compiled by Albert Seay. n.p.: American Institute of Musicology, 1975. Originally written 1477.

———. Liber de arte contrapuncti. Translated by Albert Seay. Rome: American Institute of Musicology, 1961. Originally written c. 1477.

———. [Liber de arte contrapuncti](http://earlymusictheory.org/Tinctoris/texts/deartecontrapuncti/). Translated by Jeffrey Dean. Last accessed November 16, 2015. Originally written 1477.

Trachier, Olivier. Contrepoint du XVIe siècle. Paris: Durand, 1999.

Vicentino, Nicola. Ancient music adapted to modern practice (L’antica musica ridotta alla moderna prattica). Translated by Maria Rika Maniates and edited by Claude Palisca. New Haven, Yale University Press 1996. Originally published 1555.

Zarlino, Gioseffo. Art of Counterpoint. Translated by Guy Marco and Claude Palisca, edited by Claude Palisca. New Haven and London: Yale University Press, 1968. Originally published: 1558.
