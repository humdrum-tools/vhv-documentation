---
title: Encoding ties in Humdrum
lang: en
ref: humdrum-getting_started-ties
author: Craig Stuart Sapp
translator: 
keywords: humdrum encoding tutorial ties
creation_date: 20 Aug 2017
translation_date: 
last_updated: 7 Dec 2019
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: How to encode ties in **kern data.
sidebar: main_sidebar
permalink: /humdrum/ties/index.html
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
[4e
4e]
!LO:T:dash
[4e
4e]
=2
[4e
4e]
!LO:T:dot
[4e
4e]
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

## Disjunct tied notes ##

Sometimes ties connect two notes that are not directly adjacent.  This
usually occurs in the case of written out arpeggios.  In such cases, double
the tie signifier to indicate that the ending note of the tie does not
directly follow the starting note of the tie.


{% include verovio.html
	humdrum-min-height="175px"
	source="tiedisjunct"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="tiedisjunct">
**kern
*M4/4
[[16cL
[[16e
[[16g
[16ccJ
2.c]] 2.e]] 2.g]] 2.cc]
=
*-
</script>

Notice that the last sixteenth note is adjacent to the chord to
which all of the notes are tied, so it has a regular tie
signifier.


## Cross-staff tied notes ##

Cross-staff ties (in particular for piano music), can be created
using an RDF record as in the following example:


{% include verovio.html
	humdrum-min-height="250px"
	source="tielinked"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="tielinked">
**kern	**kern
*clefF4	*clefG2
*M4/4	*M4/4
=1	=1
2F	4f
.	N[4B<
2BN]	4g
.	4f
=	=
*-	*-
!!!RDF**kern: N = linked
!!!RDF**kern: < = below
</script>

The RDF record `N = linked` is used to create the link between the two
tie endpoints in the data.  The link signifier must come immediately
in front of the tie signifiers in the data.  And the matching tie can be
either adjacent or disjunct on the other staff.


