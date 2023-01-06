
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
8cc#	6
8r	r
8dd#	7
8r	r
4ee	1
=	=
*-	*-
</script>

The interpretation `*E:` means E major.  You should preferably
include this key designation in both `**kern` and `**deg` spines
for more detailed analyses.  Other examples of keys include `*B-:`
for B&#x266d; major and `*F#:` for F&#x266f; major.  Minor keys use
a lower-case letter for the tonic (see discussion for minor keys
below).

### Rests ###

Rests can be indicated by the letter `r`.  As an extension to the
`**deg` data format, the letter `R` can be added after `r` to
indicate that the rest is longer than a particular threshold that
is given by a tandem interpretation such as `*irest<4` which means
small (ignored) rests are shorter than a quarter note (represented
in the data at `r`, or explicitly by `rr` to differentiate between
unthresholded rests which are always a single `r`. Rests a quarter
note or larger are then labeled as `rR` for a "big" rest.  The
threshold can also be inclusive such as `*irest<=4` which means
that small rests are a quarter note or shorter, while big rests are
greater than a quarter note.  Note that the rhythm value given in
the `*irest` interpretation is in the form of a `**recip` value.


{% include verovio.html
	source="restex"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
	tabsize="9"
%}
<script type="application/x-humdrum" id="restex">
**kern	**deg	**deg
*clefG2	*	*
*M4/4	*	*
*k[]	*	*
*C:	*C:	*
=1	=1	=1
*	*irest<4	*irest<=4
4c	1	1
4d	2	2
4r	rR	rr
4f	4	4
4g	5	5
8a	6	6
8r	rr	rr
8b	7	7
8r	rr	rr
4cc	1	1
=	=	=
*-	*-	*-
</script>

In the first `**deg` spine, rests less than a quarter note are labeled `rr`, while
rests a quarter note or larger are labeled as `rR`.  In the second `**deg` spine,
rests a quarter note and shorter are labeled with `rr` and rests longer than
a quarter note are labeled as `rR`.

Rests are not currently rendered in music notation and are primarily
useful for analysis of scale degree melodic contours.  The rest
duration threshold can be used to allow melodic approaches and
departures across small rests.  The default setting is `*irest<0`,
meaning that rests of any duration cannot be crossed when calculating
melodic approach or departure contours.

More information is given below for how approaches and departures
can encode rest information into the non-rest scale degree tokens.

If you want to display rests in music notation, add a zero after `r`, `rr`  or `rR`.
This will cause scale degree "0" to be displayed in the music notation:

{% include verovio.html
	source="restexzero"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
	tabsize="9"
%}
<script type="application/x-humdrum" id="restexzero">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*irest<4
4c	1
4d	2
4r	rR0
4f	4
4g	5
8a	6
8r	rr
8b	7
8r	rr
4cc	1
=	=
*-	*-
</script>

This `0` rest labeling can be done automatically with the <a
href="/filter/shed">shed</a> filter.  In the following example long
rests are marked in the score with `0` while the short rests remain
unmarked:

{% include verovio.html
	source="restexzeroauto"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
	tabsize="9"
%}
<script type="application/x-humdrum" id="restexzeroauto">
!!!filter: shed -x deg -e "s/rR/rR0/g"
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*irest<4
4c	1
4d	2
4r	rR
4f	4
4g	5
8a	6
8r	rr
8b	7
8r	rr
4cc	1
=	=
*-	*-
</script>



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

Octave subscripts can be suppressed by adding an `*Xoctave` interpretation.  The `*octave` interpretation
can be used to display octave information again:

{% include verovio.html
	source="octavex"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="octavex">
**kern	**degree
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*Xoctave
4c	1/4
4d	2/4
4e	3/4
4f	4/4
4g	5/4
*	*octave
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
| -e        | Use the following <a href="https://en.wikipedia.org/wiki/Sed" target="_blank">sed</a>-like regular expression substitution |
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


#### Displaying alterations as arrows ####

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
This style can be canceled by the interpretation `*Xcircle`.   Circles are 
typically drawn around scale degrees of a bass line.

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
This style can be canceled by the interpretation `*Xbox`.   

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
This style can be canceled by the interpretation `*Xhat`.  Hats are typically given to the
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
