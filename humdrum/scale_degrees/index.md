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
datatable: "true"
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



#### Using shed filter with scale degrees ####

If you are using `**degree` data but do not want to see the octave
information in the musical score, the <a href="/filter/shed">shed</a> filter is an easy way
of removing them before printing (but they remain in the original file):

{% include verovio.html
	source="degreenooct"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="degreenooct">
!!!filter: shed -x degree -e "s/\/\d+//g"
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

Meaning of the components in the shed filter:

| Component | Meaning |
| --- | --- |
| -x degree | Only process `**degree` spines. |
| -e        | Use the following <a href="https://en.wikipedia.org/wiki/Sed" target="_blank">sed</a>-like regular expression substition |
| "..."     | quotes are optional in this case, but it is usually a good idea to include them always.  They are required if spaces are found in the regular expression or substitution, for example. |
| s/X/Y/g   | Substitute whenever pattern X is found in the string, replace it with the string Y, and do this for all cases on the line (g = "global"). |
| \/\d+     | This is the search string which means a slash followed by one or more digits. The backslash in front of the characters are required to two reasons.  For the slash, it is needed to avoid confusing it with the outer s/X/Y/g delimiter between the X and the Y.  A plain `d` without a slash means the letter `d`, while `\d` means one of the digits from 0 through 9. |
|           | There is nothing between the last two slashes which means replace the match (X) with nothing. |


By default, the input Humdrum data in score (left side of the editor) remains unchanged when there are filters in the file.  
If you want to see the result of the filter, press control-c (Windows) or option-c (MacOS) to "compile" the filter and replace
the original file with the output of the filtering process.  The `!!!filter:` line will change to `!!!filter:` to indicate that
the filter has already been processed.

To convert `**degree` spines to `**deg` spines, you can use this filter:

```
!!!filter: shed -x degree -e "s/\/\d+//g; s/^degree$/deg/X"
```

The `X` qualifier on the second substitution command means only process exclusive interpretation tokens.

If you want to see the literal text of a `**deg` or `**degree` spine, then use this filter:

```
!!!filter: shed -e "s/degree/cdata-degree/X"
```

"cdata" means "chord-like data", and the subtype is degree (which is optional).

{% include verovio.html
	source="degreenooct"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="degreenooct">
!!!filter: shed -e "s/degree/cdata-degree/X"
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



### Chromatic alterations ###

A plus sign (`+`) can be added after the scale degree number to
indicate that it is one semitone higher than the default position
in the current key.  Two plus signs (`++`) means that the scale
degree is two semitones above the default position in the key.

Likewise `-` and `--` (minus signs) can be used to indicate that
the scale degree is one or two semitones lower than the default
position for the degree in the key.

#### Displaying alterations as accidentals ####

{% include verovio.html
	source="altacc"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="altacc">
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
4g	5
4a-	6-
4b--	7--
4cc	1
=	=
*-	*-
</script>

It is still to be decided if the accidental should come before or after the scale degree in
the music notation display (and/or should there be a tandem interpretation to control which
side the scale degree the accidental should be displayed.  It is also still to be decided if
the accidental should be relative or absolute.  In the current implementation it is relative,
meaning that it indicates the number of semitones in the alteration.  An absolute display
(not implemented) would be to show the accidental of the pitch class in the music notation.
Absolute display will be more complicated since the key designation is required before the
scale degree in order to determine the default scale degree accidental first.


#### Displaying alterations as up/down ####

To display alterations as up/down arrows after the scale degrees, use the 
`*arrow` tandem interpretation.  `*Xarrow` can be used to return to the 
default accidental display for alterations.

{% include verovio.html
	source="arrowalt"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="arrowalt">
**kern	**deg
*clefG2	*arrow
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2
4e-	3-
4f#	4+
4g	5
4a-	6-
4b--	7--
4cc	1
=	=
*-	*-
</script>

Notice that two semitone alterations are displayed as a double-tailed arrow.


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



#### Boxes ####

Boxes can be drawn around scale degrees by adding the `*box` interpretation.
This style can be cancelled by the interpretation `*Xbox`.   

{% include verovio.html
	source="boxdeg"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="boxdeg">
**kern	**deg
*clefG2	*box
*M4/4	*
*k[f#c#g#d#]	*
*E:	*E:
=1	=1
4e	1
4f#	2
4g#	3
4a	4
4b	5
*	*Xbox
4cc#	6
4dd#	7
4ee	1
=	=
*-	*-
</script>

Boxes and circles are currently mutually exclusive, so only the most recent `*box` or
`*circle` interpretation will be followed.   This may change in the future, so if you
only want circles or boxes to be displayed on a scale degree and not both, use `*Xcircle` 
before `*box`, and `*Xbox` before `*circle` to maintain a consistent rendering in the
future.



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

Proper display of the hat will depend on what font is used; otherwise, the hat will follow the digit.



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
*clefG2	*arrow
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

## Major/minor mode markers ##

`M` and `m`.  To be documented.


### Harmonic and natural minor ###

If you want to display the scale degrees in music notation using the natural minor scale, 
add the interpretation `*minnat`.   This means that the scale degrees are based on the
natural minor scale, with `7` and `7n` meaning a minor 7th and `7+` and `7h` meaning
a major seventh.  The interpretation `*minhar` can be used to explicitly indicate
that the harmonic minor is the prototype scale (or you can switch between the
two systems in a single spine by alternating between `*minnat` and `*minhar`.

{% include verovio.html
	source="minchange"
	humdrum-min-height="325px"
	scale="40"
	tabsize="11"
	pageWidth="1300"
%}
<script type="application/x-humdrum" id="minchange">
**kern	**deg	**text
*clefG2	*minnat	*v:**deg:
*M4/4	*arrow	*vv:**deg:
*k[b-e-a-]	*circle	*color:silver
*c:	*c:	*c:
=	=	=
!!LO:TX:a:t=**minnat:color=crimson
!!LO:TX:a:t=Natural minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4b-X	7	7
4b-X	7n	7n
4b-X	7h-	7h-
4cc	1	1
=	=	=
!!LO:TX:a:t=Harmonic minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4bn	7	7
4bn	7h	7h
4bn	7n+	7n+
4cc	1	1
=||	=||	=||
*c	*minhar	*
!!LO:TX:a:t=**minhar:color=crimson
!!LO:TX:a:t=Natural minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4b-X	7	7
4b-X	7n	7n
4b-X	7h-	7h-
4cc	1	1
=	=	=
!!LO:TX:a:t=Harmonic minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4bn	7	7
4bn	7h	7h
4bn	7n+	7n+
4cc	1	1
==	==	==
*-	*-	*-
</script>



{% include_relative melodic-contour.md %}



{% include_relative font-styling.md %}



## Chords ##

Currently only the first note in a chord token will be displayed.



## Displaying degree data as plain text ##

The `**deg` or `**degree` spine can be renamed to `**cdata`, or
more specifically to `**cdata-deg` or `**cdata-degree`.  Displaying
as `**cdata` (chord-like data) will show the tokens as text in the
notation:


{% include verovio.html
	source="degtext"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="degtext">
**kern	**deg	**cdata-deg
*clefG2	*arrow	*v:**deg:
*M4/4	*	*
*k[]	*	*
*C:	*C:	*C:
=1	=1	=1
4c	1	1
4e	^^3	^^3
4f#	^4+	^4+
4g	^5	^5
4e	vv3	vv3
4a	^^6	^^6
4cc	^^1	^^1
=	=	=
*-	*-	*-
</script>

The `-deg` suffix on `**cdata` is optional.  It will be conveyed
to the final SVG image as the `deg` class, and with this information
the degree data can be extracted from the SVG image or stylized
with CSS in the image.


Here is an example of automating the display of `**deg` data as
text instead of formatted scale degrees:

{% include verovio.html
	source="plaindeg"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="plaindeg">
!!!filter: shed -e "s/deg/cdata/X"
**kern	**deg
*clefG2	*arrow
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4e	^^3
4f#	^4+
4g	^5
4e	vv3
4a	^^6
4cc	^^1
=	=
*-	*-
</script>


{% include_relative embedded-verovio-options.md %}


## To do ##

* Implement key labels at key designation changes.
* Implement horizontal lines between degrees.
* melodic approaches across rests
* differentiate between repeated notes, secondary tied notes, initial notes



## Signifier summary ##


{% include signifiertable.html
	contentId="summary"
%}
<script type="text/JSON" id="summary">
{% include_relative degreeSignifiers.json %}
</script>


