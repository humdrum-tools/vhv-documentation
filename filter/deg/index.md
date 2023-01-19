---
title: deg filter
lang: en
ref: filters-deg
author: Craig Stuart Sapp
translator: 
creation_date: 19 Jan 2023
translation_date: 
last_updated: 19 Jan 2023
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/deg/index.html
---

The deg filter analyzes scale degrees in `**kern` data.  The deg
filter is similar to the `deg` tool in the Humdrum Toolkit, with
notable exceptions being that the default output of the `deg` filter
interleaves the `**deg` analysis spines within the input score so
that they can be viewed along with the music in VHV.  Also, the
default minor scale used in the `deg` filter is the natural minor,
while in the Humdrum Toolkit it is the harmonic minor.  In addition
there are lots of styling options and enhancements described for
the `**deg` representation on [this page](/humdrum/scale_degrees)
and also summarized below.

Here is a basic example of scale degrees in C major:

{% include verovio.html
	source="cmajor"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="cmajor">
!!!filter: deg
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>

And in A minor:

{% include verovio.html
	source="aminor"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="aminor">
!!!filter: deg
**kern
*k[]
*a:
4A
4B
4c
4d
4e
4f
4g
4a
=
*-
</script>

The interpretation `*C:` indicates that the music is in C major, so the `deg`
tool will set scale degree 1 to C pitch classes. `*a:`  indicates A minor,
so the pitch class A is the starting scale degree.  Note that both examples
have a key signature with zero sharps or flats: `*k[]`.  The key signature
is not used in the analysis of scale degrees; only the key designation
interpretations, such as `*C:` or `*a:` are used.


{% include_relative chromatic-alterations.md %}


{% include_relative keys.md %}


{% include_relative selective-analysis.md %}



## Extracting/showing only scale degree analyses ##

The `-I` option can be used to output only `**deg` spines instead
of embedding them in the input score.  This option by itself cannot
be displayed as music notation (currently, but may be implemented
in the future).

You can add the `--recip` option to output a timelines for the
`**deg` spines.   This is also not yet displayable, but you can add
`--kern` to display an invisible staff line to display in VHV.


{% include_relative octaves.md %}


{% include_relative ties.md %}


{% include_relative rests.md %}


{% include_relative styling.md %}



