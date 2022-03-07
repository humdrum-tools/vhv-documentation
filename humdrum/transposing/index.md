---
title: Transposing parts
lang: en es
ref: humdrum-transposing
author: Craig Stuart Sapp
translator: 
keywords: humdrum transposing parts
creation_date: 25 Jan 2018
translation_date: 
last_updated: 25 Jan 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode transposing parts in Humdrum scores.
sidebar: main_sidebar
permalink: /humdrum/transposing/index.html
---


Humdrum scores are always written in sounding pitch.  If you want to be 
able to display a transposing score, then add transposition information to each part that transposes.  A transposing interpretation start with the 
string `*ITr` followed by diatonic/chromatic description of the interval
needed to produce the written score.  For example a B-flat instrument needs 
to be written up a major second from its sounding pitches.  This means going
up one diatonic pitch name, or going up two chromatic semi-tones.  So the final
transposing interpretation is `*ITrd1c2`.  For an instrument in F, the 
transposition would be up 4 diatonic steps, equal to 7 semi-tones for an
interpretation of `*ITrd4c7`.

{% include verovio.html
	source="transpose"
	humdrum-min-height="560px"
	scale="55"
	tabsize="10"
	pageWidth="1000"
%}

<script type="application/json" id="transpose">
**kern	**kern	**kern
*part3	*part2	*part1
*staff3	*staff2	*staff1
*I"in C	*I"in F	*I"in Bb
*clefF4	*clefG2	*clefG2
*	*ITrd4c7	*ITrd1c2
*k[b-e-]	*k[b-]	*k[b-e-]
*M3/4	*M3/4	*M3/4
*MM120	*MM120	*MM120
4r	4r	4ee-
=1	=1	=1
2.r	2.r	4dd
.	.	4cc
.	.	4b-
=2	=2	=2
2.r	4r	4a
.	.	8qcc
.	4r	4b-
.	4c	4a
=3	=3	=3
2GG	4B-	2.g
.	4A	.
4r	4G	.
=4	=4	=4
2.r	4F#	4a
.	4G	4b-
.	4F	4b 4aa-
=5	=5	=5
2C	4E-	4cc 4gg
.	4r	4ff
4r	4r	4ee-
=6	=6	=6
2GG 2G	4f 4g	4dd
.	.	8qff
.	4r	4ee-
4r	4f	4dd
=7	=7	=7
2C	4e-	4cc
.	4d	4r
4r	4c	4r
=8	=8	=8
2.r	4BX	4dd
.	4c	4ee-
.	4B-	4dd- 4een 4gg
=9	=9	=9
2FF	4A	4cc 4ff
.	4G	4b- 4ee-
4r	4F	4a 4dd
=10	=10	=10
4r	4E-	4g 4cc
.	.	8qee-
4r	4F	4a 4dd
[4FF	4E-	4g 4cc
=11	=11	=11
*	*	*^
4FF]	4D	2.b-	4f
4EE- 4E-	4r	.	4g
4DD 4D	4r	.	4f
*	*	*v	*v
=12	=12	=12
4CC 4C	4r	2e- 2f# 2a
8qEE-\	.	.
4DD 4D	4r	.
4CC 4C	4f#	4ee-
=13	=13	=13
4BBB- 4BB-	4g	4dd
4AAA 4AA	4f#	4cc
4GGG 4GG	4g	4b-
=14	=14	=14
*	*	*^
2CC 2C	2e-	4a	2g
.	.	8qcc\	.
.	.	4b-	.
4DD 4D	4c	4a	4f#
*	*	*v	*v
=15	=15	=15
2.GG	2.B-	2.d 2.g
==	==	==
*-	*-	*-
</script>

In the above example score, the second part simulates a French horn part
in the key of F, but typically with a horn part, there is no key signature
and it is omitted from the score (otherwise it should show one B-flat 
in the key signature).

When playing back a score containing transposing instruments in VHV, the MIDI 
conversion will be a sounding score.

## MusicXML import ##

MusicXML files containing transposing parts will be handled properly when
the files are converted into Humdrum data by drag-and-dropping the files
onto the VHV webpage.  Notes are transposed from written pitch to
sounding pitch during the conversion process.

Try downloading [this file](Transposing.xml), containing the example score 
in MusicXML format, and then dragging it into the VHV editor.

## MEI export ##

When converting into MEI data, notes are stored in transposed form,
and the header for each part contains the transposition information
for converting to sounding pitch (so a B-flat instrument written part
would be transposed down a diatonic step equal to two semi-tones down to 
produce the sounding pitches).



