---
title: Encoding ties in Humdrum
lang: en
ref: humdrum-getting_started-ties
author: Craig Stuart Sapp
translator: 
keywords: humdrum encoding tutorial ties
creation_date: 20 Aug 2017
translation_date: 
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: How to encode ties in **kern data.
sidebar: main_sidebar
permalink: /humdrum/ties.html
---

{% include humdrum/ties.txt %}


## Tie orientation ##

There are two ways to control the placement of ties on the staff.  When
a tie needs to be placed in an arbitrary position, use one of the following
two systems.

### By layout parameters ###


{% include verovio.html
	humdrum-min-height="315px"
	source="tielayoutpos"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tielayoutpos">
**kern
*M4/4
=1
[4f
4f]
!LO:T:a
[4f
4f]
=2
[4ff
4ff]
!LO:T:b
[4ff
4ff]
==
*-
</script>

The `!LO:T:` layout prefix indicates that the layout parameter applies
to the tie in the next data token in the spine.  To force the tie above
the staff, add the parameter `a`, which is short for `a=true`.  To force the
tie below the staff, add the parameter `b`.

### By RDF records ###

When tie orientations need to be adjusted often in a score, a more
compact way of encoding them is to use an RDF record:

{% include verovio.html
	humdrum-min-height="325px"
	source="tierdf"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tierdf">
**kern
*M4/4
=1
[4f
4f]
[>4f
4f]
=2
[4ff
4ff]
[<4ff
4ff]
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>

In the above example, the `<` character is defined as a qualification
on the tie to force it below the staff, and `>` is used to force
the tie above the staff.  These characters must immediately follow
the `[` (or '_') character representing the tie start.  Other positions in
the token will cause slur or beam to be oriented up or down, and
placing the above/below signifiers after a note will move it to the
next staff above or below the current one.


### Ties on chords ###

When a chord possesses two or more ties, they can be oriented above or below
using either of the two methods described above.  For controlling the orientation
using a layout command, add `n=1` to the layout parameter to modify only the 
tie on the first note, `n=2` for the second note, and so on.

{% include verovio.html
	humdrum-min-height="425px"
	source="tiechord"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiechord">
**kern
*M4/4
=1
[4f [4a [4c
4f] 4a] 4c]
[>4f [>4a [>4c
4f] 4a] 4c]
=2
!LO:T:n=1:a
!LO:T:n=2:a
!LO:T:n=3:a
[4f [4a [4c
4f] 4a] 4c]
!LO:T:n=1:b
!LO:T:n=2:b
!LO:T:n=3:b
[4f [4a [4c
4f] 4a] 4c]
==
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


## Dashed and dotted ties ##

Layout parameters can be prefixed to the starting token of a tie
to display the tie as dotted or dashed lines.

{% include verovio.html
	humdrum-min-height="325px"
	source="tiedashdot"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiedashdot">
**kern
*M4/4
=1
[4f
4f]
!LO:T:dash
[4f
4f]
=2
[4f
4f]
!LO:T:dot
[4f
4f]
==
*-
</script>

The layout prefix `!LO:T:` means that the layout parameter applies
to a tie in the next data token.  To display the tie as a dashed
line, add the parameter `dash` which is equivalent to `dash=true`.
To display the tie as a dotted line, add the parameter `dot`.


## Coloring ties ##

Ties can be colored by giving an SVG color as a `color` layout parameter:

{% include verovio.html
	humdrum-min-height="375px"
	source="tiecolor"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="tiecolor">
**kern
*M4/4
=1
!LO:T:color=chartreuse
[2f
2f]
=2
!LO:T:dot
!LO:T:a
!LO:T:color=hotpink
[2f
2f]
=2
!LO:T:n=1:dot:color=chartreuse
!LO:T:n=2:dash:color=hotpink
[2c [2g
2c] 2g]
==
*-
</script>


