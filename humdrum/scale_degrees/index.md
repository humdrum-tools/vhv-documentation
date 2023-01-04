---
title: Scale degrees
lang: en 
ref: humdrum-scale_degrees
author: ["Craig Stuart Sapp", "author 2"]
translator: 
keywords: humdrum scale degrees
creation_date: 31 Dec 2022
translation_date:
last_updated: 31 Dec 2022
tags: [all, humdrum, scale degrees]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode scale degrees in **deg and **degree spines.
sidebar: main_sidebar
permalink: /humdrum/scale_degrees/index.html
---

Scale degrees can be encoded in Humdrum data using the `**deg` or
`**degree` exclusive interpretations.  The difference between these two
representation is that `*degree` also encodes octave information,
while `**deg` does not.

## Scale degrees ##

Here is a basic example of encoding scale degrees, which are
integers in the range from&nbsp;1 through&nbsp;7:

{% include verovio.html
	source="scale"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="scale">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2
4e	3
4f	4
4g	5
4a	6
4b	7
4cc	1
=	=
*-	*-
</script>

Scale degrees are relative to the tonic of a key.  Below are the
scale degrees for E major, where scale degree `1` now represents
the pitch class `E` instead of `C` in C major.

{% include verovio.html
	source="emajor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="emajor">
**kern	**deg
*clefG2	*
*M4/4	*
*k[f#c#g#d#]	*
*E:	*E:
=1	=1
4e	1
4f#	2
4g#	3
4a	4
4b	5
4cc#	6
4dd#	7
4ee	1
=	=
*-	*-
</script>

The interpretation `*E:` means E major.  You should preferrably
include this key designation in both `**kern` and `**deg` spines.
Other examples of keys include `*B-:` for B&#x266d; major and `*F#:`
for F&#x266f; major.  Minor keys use a lower-case letter for the
tonic (see discussion for minor keys below).

### Octaves ###

If the `**degree` exclusive interpretation is used, octave information
will be displayed as subscripts after the scale degree:

{% include verovio.html
	source="degreeoct"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="degreeoct">
**kern	**degree
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1/4
4d	2/4
4e	3/4
4f	4/4
4g	5/4
4a	6/4
4b	7/4
4ee	1/5
=	=
*-	*-
</script>





### Styling scale degrees ###

By default scale degrees are displayed as plain numbers, but other 
notation rendering styles can be given to them.  


#### Circles ####

Circles can be drawn around scale degrees by adding the `*circle` interpretation.
This style can be cancelled by the interpretation `*Xcircle`.   Circles are 
typically drawn around scale derees of a bass line.

{% include verovio.html
	source="circleddegrees"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="circleddegrees">
**kern	**deg
*clefG2	*circle
*M4/4	*
*k[f#c#g#d#]	*
*E:	*E:
=1	=1
4e	1
4f#	2
4g#	3
4a	4
4b	5
*	*Xcircle
4cc#	6
4dd#	7
4ee	1
=	=
*-	*-
</script>

#### Hats ####

Hats (carets, circumflexes)  can be drawn above scale degrees by adding the `*hat` interpretation.
This style can be cancelled by the interpretation `*Xhat`.  Hats are typically given to the
melodic part's scale degrees.

{% include verovio.html
	source="hatdeg"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="hatdeg">
**kern	**deg
*clefG2	*hat
*M4/4	*
*k[f#c#g#d#]	*
*E:	*E:
=1	=1
4e	1
4f#	2
4g#	3
4a	4
4b	5
*	*Xhat
4cc#	6
4dd#	7
4ee	1
=	=
*-	*-
</script>

Proper display of the hat will depend on what font is used.

#### Staff placement ####

By default scale degrees are displayed below the staff, but they can be show above by adding the `*above`
interpretation.  The `*below` interpretation can move the degree display below the staff again.

{% include verovio.html
	source="placement"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="placement">
**kern	**deg
*clefG2	*above
*M4/4	*
*k[f#c#g#d#]	*
*E:	*E:
=1	=1
4e	1
4f#	2
4g#	3
4a	4
4b	5
*	*below
4cc#	6
4dd#	7
4ee	1
=	=
*-	*-
</script>


## Scale degrees in minor keys ##

Minor keys use a lowercase letter in their key designations, such
as `*c:` for C minor and `*f#:` for F&#x266f; minor.  Note that the
harmonic minor is the prototype scale for minor keys (not the natural
minor).  The harmonic minor has a major 7th interval between the
tonic and the 7th scale degree, forming a lead tone to the tonic.

{% include verovio.html
	source="harminor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="harminor">
**kern	**deg
*clefG2	*
*M4/4	*
*k[b-e-a-]	*
*c:	*c:
=1	=1
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4bn	7
4cc	1
=	=
*-	*-
</script>

To allow conversion between harmonic and natural minors, add `h` after a `7` scale degree
to confirm that it is a major seventh above the first scale degree (or a minor second below
the first scale degree).  To encode a 7th scale degree in a natural minor key, add `n` after the `7` 
for a minor seventh above or major second below the first scale degree.

{% include verovio.html
	source="bothminor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="bothminor">
**kern	**deg
*clefG2	*
*M4/4	*
*k[b-e-a-]	*
*c:	*c:
=1	=1
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b	7h
4cc	1
=1||	=1||
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b-	7n
4cc	1
=	=
*-	*-
</script>

`7n` implies B-flat, and since the display is set to C harmonic minor, the `n` causes a flat to 
be displayed for the 7th scale degree (`n` or `h` on any other scale degree will be ignored).



## Changing display between harmonic an natural minor ##

If you want to display the scale degrees in music notation using the natural minor scale, 
add the interpretation `*minnat`.   This means that the scale degrees are based on the
natural minor scale, with `7` and `7n` meaning a minor 7th and `7+` and `7h` meaning
a major seventh.  The interpretation `*minhar` can be used to explicitly indicate
that the harmonic minor is the prototype scale (or you can switch between the
two systems in a single spine by alternating between `*minnat` and `*minhar`.

{% include verovio.html
	source="minchange"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="minchange">
**kern	**deg
*clefG2	*minnat
*M4/4	*arrow
*k[b-e-a-]	*
*c:	*c:
=	=
!!LO:TX:a:t=Natural minor degree display
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b-	7
4b-	7n
4b-	7h-
4cc	1
=||	=||
!!LO:TX:a:t=Harmonic minor degree display
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b	7
4b	7h
4b	7n+
4cc	1
==	==
*-	*-
</script>



## Chromatic alterations ##

If a pitch is outside of a key's scale, then a `+` sign
should be added after degree for each semitone raised
from the default degree's postion in the scale.  To lower
by a semitone, use `-`, or `--` when the note is lowered
two scale degrees from its default position.

{% include verovio.html
	source="alteration"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="alteration">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2
4e-	3-
4f#	4+
4g##	5++
4a--	6--
4b	7
4cc	1
=	=
*-	*-
</script>

### Styling chromatic alterations ###

By default chromatic alterations are show as accidentals, but the
interpretation `*arrow` can be used to show alterations as up/down
arrows after the scale degree:

{% include verovio.html
	source="arrow"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="arrow">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*arrow
4c	1
4d	2
4e-	3-
4f#	4+
4g##	5++
4a--	6--
4b	7
4cc	1
=	=
*-	*-
</script>



## Melodic approach ##

The interval from the previous melodic note to the current note of
the scale degree can be encoded as `^` if the interval rises to the
scale degree, or `v` if it falls. 

{% include verovio.html
	source="updown"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="updown">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	^2
4e	^3
4f	^4
4g	^5
4f	v4
4e	v3
4d	v2
4c	v1
=	=
*-	*-
</script>


### Step v. Leap

The up/down melodic approach signifiers can be doubled to indicate melodic leaps (motion by a third 
or more).

{% include verovio.html
	source="leapstep"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="leapstep">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4e	^^3
4d	v2
4f	^^4
4a	^^6
4g	v5
4f	v4
4d	vv2
4c	v1
=	=
*-	*-
</script>


## Melodic departure ##

Melodic departure information can be encoded using `/` for the next note up and `\` for the
next note down.

{% include verovio.html
	source="departure"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="departure">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1//
4e	3\
4d	2//
4f	4//
4a	6\
4g	5\
4f	4\\
4d	2/
4c	1
=	=
*-	*-
</script>

Here is an example of encoding both approach and departure intervals:

{% include verovio.html
	source="departure"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="departure">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1//
4e	^^3\
4d	v2//
4f	^^4//
4a	^^6\
4g	v5\
4f	v4\\
4d	vv2/
4c	v1
=	=
*-	*-
</script>



