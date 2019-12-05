---
title: Encoding slurs in Humdrum
lang: en
ref: humdrum-getting_started-slurs
author: Craig Stuart Sapp
translator: 
keywords: humdrum encoding tutorial slurs
creation_date: 20 Aug 2017
translation_date: 
last_updated: 25 Jan 2018
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
	humdrum-min-height="345px"
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

## Coloring slurs ##

Slurs can be colored by giving an SVG color as a `color` layout parameter:

{% include verovio.html
	humdrum-min-height="275px"
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
!LO:S:dot:a:color=#00ff00
(4c
4d
4e
4f)
==
*-
</script>



