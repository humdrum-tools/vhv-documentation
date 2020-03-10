---
title: System decorating
lang: en
ref: system decoration instrument names
author: Craig Stuart Sapp
translator: 
keywords: humdrum instrument names
creation_date: 24 Feb 2020
translation_date: 
last_updated: 24 Feb 2020
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of system decoration and staff names.
sidebar: main_sidebar
permalink: /humdrum/system/index.html
---

This page describes the visual aspects of scores involving braces, brackets, staff names and abbreviations,
as well as group names and abbreviations.


## Staff names ##

Staff names are given in tandem interpretations starting with the
string `*I"`.  The staff names are related to <a target="_blank">instrument
codes</a>, such as `*Icello` for the violon cello.  The staff names
are a visual description off the instrument or other text displayed
at the start of a movement, while instrument codes are for analysis
purposes.  Giving a staff name will override the display of an
automatically generated name from an instrument code at the start
of the data (but automatic staff name generation from the instrument
code is not implemented yet).

Here is an example of a string quartet score, where each of the
staff names are given (try changing the names in the text box on
the left, and they will update as you type on the right):

{% include verovio.html
	source="quartet"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="quartet">
**kern	**kern	**kern	**kern
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
</script>



## Staff abbreviations ##

After the first system in a movement, the will be no instrument names displayed on successive
systems.  An optional staff abbreviation can be given by prefixing `*I'` before the abbreviation
string for the staff.

{% include verovio.html
	source="quartet2"
	humdrum-min-width="400"
	pageWidth="1250"
	spacingLinear="0.24"
	tabsize="12"
%}
<script type="application/json" id="quartet2">
**kern	**kern	**kern	**kern
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*I'vc.	*I'vla.	*I'vln. 2	*I'vln. 1
*M4/4	*M4/4	*M4/4	*M4/4
=1	=1	=1	=1
1CC	1c	1g	1ee
=2	=2	=2	=2
1DD	1D	1f	1aa
=3	=3	=3	=3
1EE	1G	1b	1gg
=4	=4	=4	=4
1FF	1F	1a	1cc
=5	=5	=5	=5
1GG	1D	1g	1b
=6	=6	=6	=6
1AA	1C	1e	1a
=7	=7	=7	=7
1BB	1D	1d	1f
=8	=8	=8	=8
1C;	1C;	1e;	1g;
==	==	==	==
*-	*-	*-	*-
</script>


## System styling ##

### Default styling ###

When the system contains only a single staff, no decoration is added to the system:

{% include verovio.html
	source="single"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="single">
**kern
*I"Cello
*I'vc.
*M4/4
=1
1CC
=2
1DD
=3
1EE
=
*-
</script>


When the system contains two staves, a brace will automatically be added, and the
staves will be barred together (although this should not be done if there are lyrics
attached to the top staff).

{% include verovio.html
	source="double"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="double">
**kern	**kern
*part1	*part1
*I"Piano	*I"Piano
*M4/4	*M4/4
=1	=1
1CC	1ee
=2	=2
1DD	1b
=3	=3
1EE	1g
=	=
*-	*-
</script>

When there are three or more staves, a bracket will automatically be added, but the
staves will not be barred together.

{% include verovio.html
	source="triple"
	humdrum-min-height="250"
	tabsize="12"
%}
<script type="application/json" id="triple">
**kern	**kern	**kern
*I"part 3	*I"part 2	*I"part 1
*M4/4	*M4/4	*M4/4
=1	=1	=1
1CC	1ee	1gg
=2	=2	=2
1DD	1b	1ff
=3	=3	=3
1EE	1g	1ee
=	=	=
*-	*-	*-
</script>


## System decoration ##

To override the default brace/bracket and barring styles, a line starting with `!!!system-decoration:` can
give a different style.  To use this system, it is expected that all parts contain staff enumerations,
and these staff numbers are referenced in the system decoration string.


Here is an example for a string quartet, where the system decoration connects the bars on
all staves together:


{% include verovio.html
	source="barquart"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: [(s1,s2,s3,s4)]
</script>

### Staff wildcard ###

If you only need a single brace or bracket for the entire system, either barred or unbarred, then
you can use `*` to represent all staves.

{% include verovio.html
	source="barquart2"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart2">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: [(*)]
</script>

Here is an example of removing the bracket, but keeping the barring:

{% include verovio.html
	source="barquart3"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart3">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: (*)
</script>

Notice that parentheses around staves (or the wildcard symbol) will
case the staves to be barred together.

Here is an example of removing the bracket as well as the barring:

{% include verovio.html
	source="barquart4"
	humdrum-min-width="400"
	tabsize="12"
%}
<script type="application/json" id="barquart4">
**kern	**kern	**kern	**kern
*staff4	*staff3	*staff2	*staff1
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1
*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=
1CC	1c	1g	1ee
=	=	=	=
*-	*-	*-	*-
!!!system-decoration: *
</script>



### Grand staff name ###

There are several methods for giving a label to the grand staff. The first method is
to add `*part` markers in each spine followed by matching non-zero integers.

{% include verovio.html
	source="piano"
	humdrum-min-width="200"
	tabsize="12"
%}
<script type="application/json" id="piano">
**kern	**kern
*part1	*part1
*I"Piano	*
*M4/4	*M4/4
=	=
1CC	1f
=	=
*-	*-
</script>

Another method is to use group labels, which start with `*I""`,
rather than part labels, which start with `*I"`.  This also has to
be in coordination with `*group` markers indicating the staves that
should be grouped together:

{% include verovio.html
	source="piano2"
	humdrum-min-width="200"
	tabsize="12"
%}
<script type="application/json" id="piano2">
**kern	**kern
*group1	*group1
*I""Piano	*
*M4/4	*M4/4
=	=
1CC	1f
=	=
*-	*-
</script>


## Instrument class grouping ##

Instrument class tandem interpretations can be used in an equivalent manner to
`*group#` interpretations.  Here is an example:

{% include verovio.html
	source="ic"
	humdrum-min-width="600"
	humdrum-max-height="250"
	tabsize="12"
%}
<script type="application/json" id="ic">
**kern	**kern	**kern	**kern	**kern	**kern	**kern	**kern	**kern
*staff9	*staff8	*staff7	*staff6	*staff5	*staff4	*staff3	*staff2	*staff1
*ICstr	*ICstr	*ICstr	*ICstr	*ICbras	*ICbras	*ICww	*ICww	*ICww	
*I"Cello	*I"Viola	*I"Violin 2	*I"Violin 1	*I"Trombone	*I"Trumpet	*I"Bassoon	*I"Oboe	*I"Flute
*IclefF4	*IclefC3	*IclefG2	*IclefG2	*IclefF4	*IclefG2	*IclefF4	*IclefG2	*IclefG2
*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4	*M4/4
=	=	=	=	=	=	=	=	=
1CC	1c	1cc	1ccc	1C	1cc	1C	1cc	1ccc
=	=	=	=	=	=	=	=	=
*-	*-	*-	*-	*-	*-	*-	*-	*-
!!!system-decoration: [(ww)][(bras)][(str)]
</script>



