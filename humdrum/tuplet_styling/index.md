---
title: Tuplet styling
lang: en
ref: humdrum-tuplet_styling
author: Craig Stuart Sapp
translator: 
keywords: humdrum tuplet styling
creation_date: 18 Mar 2017
translation_date: 
last_updated: 18 Mar 2017
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: Visual tuplet numbers can be turned on or off for a spine.
sidebar: main_sidebar
permalink: /humdrum/tuplet_styling/index.html
---


Music notation containing a lot of tuplets will often drop tuplet
numbers after the first few occurrences of tuplets when the
rhythmic interpretation without the number remains clear.  Below
is an example of omitted triplet numbers in the first movement of
Beethoven's *moonlight* sonata.  Only the first measure contains
visible tuplet numbers, and subsequent triplets are not marked:

{% include image.html
	file="moonlight.gif"
	alt="moonlight sonata mvmt 1, mm 1-8"
	max-width="100%"
	caption="Beethoven, Moonlight sonata, mvmt.1, mm. 1&ndash;8."
%}

To turn off tuplet numbers in a Humdrum `**kern` spine, add the
tandem interpretation `*Xtuplet` somewhere in front of the first
note of a tuplet that should have a suppressed number.  To start
displaying visual tuplet numbers again in the same spine, add
the tandem interpretation `*tuplet`.

{% include verovio.html
	source="moonlight"
	scale="30"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="moonlight">
**kern	**kern
*clefF4	*clefG2
*k[f#c#g#d#]	*k[f#c#g#d#]
*c#:	*c#:
*M2/2	*M2/2
*MM54	*MM54
=1-	=1-
1CC# 1C#	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
*	*Xtuplet
=2	=2
1BBB 1BB	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
.	12G#L
.	12c#
.	12eJ
=3	=3
2AAA 2AA	12AL
.	12c#
.	12eJ
.	12AL
.	12c#
.	12eJ
2FFF# 2FF#	12AL
.	12dn
.	12f#J
.	12AL
.	12d
.	12f#J
=4	=4
2GGG# 2GG#	12G#L
.	12B#
.	12f#J
.	12G#L
.	12c#
.	12eJ
2GGG# 2GG#	12G#L
.	12c#
.	12d#XJ
.	12F#Lj
.	12B#
.	12d#J
=5	=5
*	*^
1CC# 1GG# 1C#	2r	12EL
.	.	12G#
.	.	12c#J
.	.	12G#L
.	.	12c#
.	.	12eJ
.	4r	12G#L
.	.	12c#
.	.	12eJ
!	!	!
.	8.g#L	12G#L
.	.	12c#
.	.	12eJ
.	16g#Jk	.
=6	=6	=6
1BBB# 1GG# 1BB#	2.g#	12G#L
.	.	12d#
.	.	12f#J
.	.	12G#L
.	.	12d#
.	.	12f#J
.	.	12G#L
.	.	12d#
.	.	12f#J
.	8.g#L	12G#L
.	.	12d#
.	.	12f#J
.	16g#Jk	.
=7	=7	=7
(<2CC# (>2C#	(2g#	12G#L
.	.	12c#
.	.	12eJ
.	.	12G#L
.	.	12c#
.	.	12eJ
2FFF#) 2FF#)	2a	12AL
.	.	12c#
.	.	12f#J
.	.	12AL
.	.	12c#
.	.	12f#J
=8	=8	=8
2BBB 2BB	2g#	12G#L
.	.	12B
.	.	12eJ
.	.	12G#L
.	.	12B
.	.	12eJ
2BBB 2BB	4f#	12AL
.	.	12B
.	.	12d#J
.	4b	12AL
.	.	12B
.	.	12d#J
=9	=9	=9
*	*v	*v
*-	*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

Try moving or adding `*tuplet`/`*Xtuplet` interpretations in the above 
Humdrum data to see how this affects the music notation on the right.

In the future, other parameters will probably be added to the styling 
interpretation, such as whether or not to display the tuplet numbers 
above or below stems/beams.

{% include warning.html
	content="A tuplet styling interpretation applies to an entire spine, and cannot be controlled independently within sub-spines."
%}

