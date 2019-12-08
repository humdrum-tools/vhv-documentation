---
title: Encoding slurs in Humdrum
lang: en
ref: humdrum-getting_started-slurs
author: Craig Stuart Sapp
translator: 
keywords: humdrum encoding tutorial slurs
creation_date: 20 Aug 2017
translation_date: 
last_updated: 7 Dec 2019
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: How to encode slurs in **kern data.
sidebar: main_sidebar
permalink: /humdrum/slurs.html
---

{% include humdrum/slurs.txt %}


## Slur orientation ##

There are two ways to control the placement of slurs on the staff.  When
a slur needs to be placed in an arbitrary position, use one of the following
two systems.

### By layout parameters ###


{% include verovio.html
	humdrum-min-height="315px"
	source="slurlayoutpos"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurlayoutpos">
**kern
*M4/4
=1
(4c
4d)
!LO:S:a
(4e
4f)
=2
(4cc
4dd)
!LO:S:b
(4ee
4ff)
==
*-
</script>

The `!LO:S:` layout prefix indicates that the layout parameter applies
to the slur in the next data token in the spine.  To force the slur above
the staff, add the parameter `a`, which is short for `a=true`.  To force the
slur below the staff, add the parameter `b`.

### By RDF records ###

When slur orientations need to be adjusted often in a score, a more
compact way of encoding them is to use an RDF record:

{% include verovio.html
	humdrum-min-height="325px"
	source="slurrdf"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurrdf">
**kern
*M4/4
=1
(4c
4d)
(>4e
4f)
=2
(4cc
4dd)
(<4ee
4ff)
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

In the above example, the `<` character is defined as a qualification
on the slur to force it below the staff, and `>` is used to force
the slur above the staff.  These characters must immediately follow
the `(` character representing the slur start.  Other positions in
the token will cause slur or beam to be oriented up or down, and
placing the above/below signifiers after a note will move it to the
next staff above or below the current one.

### Slurs on chords ###

When a chord possesses two slurs, the two slurs will be moved to opposite
sides of the chord automatically:

{% include verovio.html
	humdrum-min-height="325px"
	source="slurchord"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurchord">
**kern
*M4/4
=1
(2c 2e 2g
2d 2f 2a)
=2
((2c 2e 2g
2d 2f 2a))
=3
(2c 2e (2g
2d) 2f 2a)
=4
2c 2e 2g((
2d 2f 2a))
==
*-
</script>

The position of the slur in the chord is not important: the slur is attached
to the chord, not to any individual notes in the chord.


## Dashed and dotted slurs ##

Layout parameters can be prefixed to the starting token of a slur
to display the slur as dotted or dashed lines.


{% include verovio.html
	humdrum-min-height="275px"
	source="slurdashdot"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurdashdot">
**kern
*M4/4
=1
!LO:S:dash
(4c
4d
4e
4f)
=2
!LO:S:dot
(4c
4d
4e
4f)
==
*-
</script>

The layout prefix `!LO:S:` means that the layout parameter applies
to a slur in the next data token.  To display the slur as a dashed
line, add the parameter `dash` which is equivalent to `dash=true`.
To display the slur as a dotted line, add the parameter `dot`.

### Multiple slurs ###

Multiple slurs on notes or chords can be addressed individually
within the layout parameter by adding the `n` parameter set to the
number of the slur.  For example, if there are two slurs, then the
first one can be referenced by adding `n=1` to the layout parameter,
and `n=2` for the second one.

{% include verovio.html
	humdrum-min-height="415px"
	source="multiplestyle"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multiplestyle">
**kern
*M4/4
=1
!LO:S:dash
((2c 2e
2f 2cc))
=2
!LO:S:dash:n=1
((2c 2e
2f 2cc))
=3
!LO:S:dash:n=2
((2c 2e
2f 2cc))
=4
!LO:S:dash:n=1
!LO:S:dot:n=2
((2c 2e
2f 2cc))
==
*-
</script>


## Coloring slurs ##

Slurs can be colored by giving an SVG color as a `color` layout parameter:

{% include verovio.html
	humdrum-min-height="450px"
	source="slurcolor"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="slurcolor">
**kern
*M4/4
=1
!LO:S:color=hotpink
(4c
4d
4e
4f)
=2
!LO:S:dot
!LO:S:a
!LO:S:color=#00ff00
(4c
4d
4e
4f)
=2
!LO:S:n=1:dot:color=violet
!LO:S:n=2:dash:color=dodgerblue
((2c 2g
2d 2b))
==
*-
</script>


## Phrase marks ##

Phrase marks are similar to slurs but are used to mark analytic phrases
in `**kern` data.  The default rendering style for phrasing is an open bracket:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrase"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrase">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
</script>


### Phrase rendering styles ###

Phrase marks can be rendered in a variety of styles and colors as illustrated
below:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasestyles"
	scale="55"
	pageWidth="1150"
%}
<script type="application/x-humdrum" id="phrasestyles">
**kern
=1
!!LO:TX:b:t=bracket styles
{4c
4d
4e
4f}
=2
!LO:P:brack
{4c
4d
4e
4f}
=3
!LO:P:dot
{4c
4d
4e
4f}
=4
!LO:P:dash
{4c
4d
4e
4f}
=5
!LO:P:open
{4c
4d
4e
4f}
=6||
!!LO:TX:b:t=slur styles
!LO:P:slur
{4c
4d
4e
4f}
=7
!LO:P:slur:dot
{4c
4d
4e
4f}
=8
!LO:P:slur:dash
{4c
4d
4e
4f}
=9||
!!LO:TX:b:t=coloring
!LO:P:slur:dash:color=dodgerblue
{4c
!LO:P:dot:color=red
{4d
4e}
4f}
=10
!LO:P:dash:color=dodgerblue
{4c
!LO:P:dot:color=red
&{4d
4e}
4f&}
=11||
!!LO:TX:b:t=invisible
{y4c
4d
4e
4f}
=12
!LO:P:none
{4c
4d
4e
4f}
==
*-
</script>


### Default rendering style for phrases marks ###

An RDF record can be used to set the default rendering style of phrase marks.


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasedefault"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrasedefault">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
!!!RDF**kern: { = phrase, brack color=orange
</script>

Various rendering styles:

| style | result |
|-------|--------|
| `brack` | bracket |
| `dot` | dotted bracket |
| `dash` | dashed bracket |
| `none` | no bracket |
| `open` | open bracket (default) |
| `slur` | slur |
| `slur dot` | dotted slur |
| `slur dash` | dashed slur |

The default phrase style can also be given a color as in the above example.


Here is an example of suppressing phrase marks by default, but giving a local
style to the last phrase:


{% include verovio.html
	humdrum-min-height="405px"
	source="phrasenone"
	scale="55"
	pageWidth="1050"
%}
<script type="application/x-humdrum" id="phrasenone">
**kern
*M2/4
*k[b-]
*F:
{8.r
16ccL
8.ccJ
16cc
=1
4cc
4dd
=2
8.g}L
{16aJ
8.b-L
16ddJ
=3
4dd
4cc
=4
8.a}L
!LO:P:dash:color=violet
{16ccJ
8.ccL
16ffJ
=5
4ff
8.eeL
16ddJ
=6
4ee
4dd
=7
4cc
4r}
==
*-
!!!RDF**kern: { = phrase, none
</script>



