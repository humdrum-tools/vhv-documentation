---
title: mint filter
lang: en
page_language: en
author: Wolfgang Drescher
creation_date: 16 Jul 2026
last_updated: 16 Jul 2026
ref: filters-mint
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: "Calculate the melodic interval between consecutive notes in **kern spines."
permalink: /filter/mint/index.html
---

The `mint` filter calculates the melodic interval between each note and the
previous note attack within the same `**kern` voice, adding a new `**mint` spine
after every processed `**kern` spine. It is a humlib reimplementation of the
[`mint` command](https://www.humdrum.org/Humdrum/commands/mint.html) from the
original Humdrum Toolkit.

Rests are transparent for this calculation: the interval is always measured
across intervening rests and tied notes, using the last note that was actually
sounded. If a `**kern` spine contains a chord, the highest note of the chord is
used as the reference pitch by default (this can be changed with the `-l`
option).

Since the original Humdrum Toolkit already has a program called `mint`, the
compiled command-line version of this tool in humlib is named `mintx` to avoid a
naming conflict. Inside VHV both names refer to the same filter, so `!!!filter:
mint` and `!!!filter: mintx` are equivalent.

`**mint` is not a spine type with dedicated rendering support in Verovio, so to
actually see the calculated intervals in the music notation you currently need
to add the `-x` option (`--cdata`), which relabels the output spine as
`**cdata-mint`. This makes Verovio display the intervals as chord-symbol-like
text, the same way as any other [`**cdata`](/spine/cdata) spine.

Here is a basic example:

{% include verovio.html
	source="basic"
	humdrum-min-height="330px"
	humdrum-max-height="330px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="basic">
!!!filter: mint -x
**kern
*clefG2
4gg
=
2.ee
4aa
=
2.g
4ccc
=
4.e
8f
[2d
=
8dL]
8e
8f
8gJ
8g#L
8aJ
8eeL
8ddJ
=
2.cc
*-
</script>

The first note of a voice has no previous note to compare it to, so it is shown
in square brackets instead of an interval, e.g. `[gg]` for the first note of
this example. Every following note is shown as a signed interval consisting of a
direction (`+` for up, `-` for down), an interval quality (`P` perfect, `M`
major, `m` minor, `A` augmented, `AA` doubly augmented, `d` diminished, `dd`
doubly diminished), and a diatonic interval number, e.g. `+M2` for a major
second upwards or `-M9` for a compound major ninth downwards (as between the
`aa` and the following `g`). The tied `d` in the middle of the example does not
get a new interval: it is shown as a null token `.`, since it is not a new note
attack (the original Humdrum Toolkit `mint` program had a bug where tied notes
were incorrectly given an interval of `P1`; this is fixed in the humlib
version).

Rests and tied notes do not get a new interval calculated for them: rests are
shown as `r`, and tied continuations are shown as a null token `.`. Intervals
are still measured correctly across them, using the last note that was actually
sounded:

{% include verovio.html
	source="rests_ties"
	humdrum-min-height="230px"
	humdrum-max-height="230px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="rests_ties">
!!!filter: mint -x
**kern
*clefG2
4c
4d
8r
8e
[4f
4f]
2g
=
*-
</script>


The original `mint` program also replaced the `**kern` spines with the
calculated `**mint` spines, rather than adding `**mint` as an additional spine
next to `**kern`. If you want to reproduce that behavior, pipe the output of
`mint` into the [extract](/filter/extract) filter (`extractxx -I kern` on the
command line), which removes the `**kern` spines and leaves only the `**mint`
spines.


## Options ##

{% include filter-options.html file="options.aton" lang="EN" %}



<a name="option-a"></a>

## Direction of the interval ##

By default `mint` will prefix every interval with a `+` (upward motion) or `-`
(downward motion). You can hide this direction with the `-a` option
(`--absolute`).

{% include verovio.html
	source="absolute"
	humdrum-min-height="230px"
	humdrum-max-height="230px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="absolute">
!!!filter: mint -x -a
**kern
*clefG2
4gg
=
2.ee
4aa
=
2.g
4ccc
=
4.e
8f
[2d
=
8dL]
8e
8f
8gJ
8g#L
8aJ
8eeL
8ddJ
=
2.cc
*-
</script>



<a name="option-c"></a>

## Compound intervals ##

By default `mint` will display the exact distance between two notes, even if the
interval spans more than an octave (a "compound" interval, e.g. a tenth). Use
the `-c` option (`--compound`) to reduce these to simple intervals within a
single octave.

{% include verovio.html
	source="compound"
	humdrum-min-height="230px"
	humdrum-max-height="230px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="compound">
!!!filter: mint -x -c
**kern
*clefG2
4gg
=
2.ee
4aa
=
2.g
4ccc
=
4.e
8f
[2d
=
8dL]
8e
8f
8gJ
8g#L
8aJ
8eeL
8ddJ
=
2.cc
*-
</script>


<a name="option-d"></a>

## Diatonic interval number ##

By default `mint` will show the interval quality (`P`, `M`, `m`, `A`, `AA`, `d`
or `dd`) together with the diatonic interval number. If you only want the
diatonic number without the quality, use the `-d` option (`--diatonic`).

{% include verovio.html
	source="diatonic"
	humdrum-min-height="230px"
	humdrum-max-height="230px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="diatonic">
!!!filter: mint -x -d
**kern
*clefG2
4gg
=
2.ee
4aa
=
2.g
4ccc
=
4.e
8f
[2d
=
8dL]
8e
8f
8gJ
8g#L
8aJ
8eeL
8ddJ
=
2.cc
*-
</script>



<a name="option-l"></a>

## Lowest note of a chord ##

When a `**kern` spine contains chords, `mint` will by default use the highest
note of each chord to calculate the melodic interval. Use the `-l` option
(`--lowest`) to use the lowest note of each chord instead.

{% include verovio.html
	source="lowest"
	humdrum-min-height="230px"
	humdrum-max-height="230px"
	scale="50"
	tabsize="10"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="lowest">
!!!filter: mint -x -l
**kern
*clefG2
4f 4g 4b
4e 4g 4cc
=
*-
</script>



<a name="option-x"></a>

## Labeling the output spine ##

By default `mint` labels its output spine `**mint`. Since Verovio does not yet
have a dedicated renderer for `**mint` data, add the `-x` option (`--cdata`) to
relabel the spine to `**cdata-mint`, so it is displayed using the generic
[`**cdata`](/spine/cdata) rendering mechanism (which is what every example on
this page does). Without `-x` the intervals are still calculated correctly, they
just are not shown in the notation.



## Selective analysis ##

In addition to calculating intervals for all `**kern` spines in a file, the
`mint` filter can select a subset of the music to be analyzed. Spines can be
selected either by using `-s` to select the nth spine in the file, or with `-k`
to select the nth `**kern` spine in the file.



<a name="option-k"></a>

### Selecting spines with -k ###

| Example        | Meaning                                                                                              |
|----------------|------------------------------------------------------------------------------------------------------|
| `-k 1`         | Calculate intervals only for the first (leftmost) kern spine in the input data.                      |
| `-k 1,4`       | Calculate intervals for the first and fourth kern spine.                                             |
| `-k 2-4`       | Calculate intervals for the second, third and fourth kern spines.                                    |
| `-k $`         | Calculate intervals for the last kern spine.                                                         |
| `-k 3,$`       | Calculate intervals for the third and last kern spines.                                              |
| `-k 1-4,6,9-$` | Calculate intervals for the first, second, third, fourth, sixth, and ninth through last kern spines. |
| `-k $1`        | Calculate intervals for the penultimate kern spine.                                                  |
| `-k $2-$`      | Calculate intervals from two kern spines before the end to the last kern spine.                      |


<a name="option-s"></a>

### Selecting spines with -s ###

| Example        | Meaning                                                                                         |
|----------------|-------------------------------------------------------------------------------------------------|
| `-s 1`         | Calculate intervals only for the first (leftmost) spine in the input data.                      |
| `-s 1,4`       | Calculate intervals for the first and fourth spine.                                             |
| `-s 2-4`       | Calculate intervals for the second, third and fourth spines.                                    |
| `-s $`         | Calculate intervals for the last spine.                                                         |
| `-s 3,$`       | Calculate intervals for the third and last spines.                                              |
| `-s 1-4,6,9-$` | Calculate intervals for the first, second, third, fourth, sixth, and ninth through last spines. |
| `-s $1`        | Calculate intervals for the penultimate spine.                                                  |
| `-s $2-$`      | Calculate intervals from two spines before the end to the last spine.                           |
