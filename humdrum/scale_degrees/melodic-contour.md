
## Melodic approach and departure ##

Signifiers can be added to scale degree tokens that encode the basic
melodic contour the note of the scale degree forms with the previous
and/or next notes.



### Melodic approach ###

Add `^` before the scale degree if the note is approached by a step
up from a lower note (by an interval of a second with any chromatic
alteration).  Use `^^` to indicate that the note is approached by
a leap from a lower note (a third or lower than the current note).

The `v` signifier indicates an approach down by step, and `vv` means
down by leap.

{% include verovio.html
	source="approaching"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="approaching">
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
4e	vv3
4c	vv1
4G	vv5
4c	^^1
=	=
*-	*-
</script>

Stepwise motion is indicated by a thin diagonal arrow pointing in
the direction of the approach.  Leaps are displayed as thick diagonal
arrows, also pointing in the direction of the approach.



### Melodic departure ###

Add a single quote (`'`) after the scale degree and alteration if
the note is followed by a step up to a higher note (by an interval
of a second).  Use two single quotes (`''`) to indicate that the
note is departed by a leap to a higher note (a third or higher than
the current note).

A comma (`,`) signifier indicates a departure down by step, and
double comma `,,`  means down by leap.

{% include verovio.html
	source="departing"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="departing">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1'
4d	2'
4e	3'
4f	4'
4g	5,,
4e	3,,
4c	1,,
4G	5''
4c	1
=	=
*-	*-
</script>

Stepwise motion is indicated by a thin diagonal arrow pointing in
the direction of the departure.  Leaps are displayed as thick
diagonal arrows, also pointing in the direction of the departure.

Both approaches and departures can be encoded and displayed at the same time:

{% include verovio.html
	source="both"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="both">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1'
4d	^2'
4e	^3'
4f	^4'
4g	^5,,
4e	vv3,,
4c	vv1,,
4G	vv5''
4c	^^1
=	=
*-	*-
</script>


### Gross versus refined contours ###

The Humdrum Toolkit `deg` tool does not distinguish between leaps and
steps (so these currently have to be encoded by hand).   Instead
the signifer `^` is used for both leaps and steps, as well as 
for `v`.

To explicitly indicate that the melodic contours do not distinguish
between steps and leaps, add the `*gross` tandem interpretation to
indicate that the data encodes gross melodic contours.

If you want to explicitly indicate that the data does encode refined
contours (i.e., distinguishing between steps and leaps), then add
the `*refined` tandem interpretation.  The presence of double 
signifiers for melodic contours will otherwise indirectly indicate
that refined melodic contours are being encoded.

If you have data encoded with both leaps and steps, but you want
to show both with the same arrow style, then the <a
href="/filter/shed">shed</a> filter can be used to select thin or
thick arrows for both steps and leaps:

{% include verovio.html
	source="singlearrows"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="singlearrows">
!!!ONB: thin arrows for both steps and leaps
!!!filter: shed -x deg -e "s/\^+/^/g; s/v+/v/g"
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
4e	vv3
4c	vv1
4G	vv5
4c	^^1
=	=
*-	*-
</script>

Here is an example to show all approaches as thick arrows:

{% include verovio.html
	source="thickarrows"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="thickarrows">
!!!ONB: thin arrows for both steps and leaps
!!!filter: shed -x deg -e "s/\^+/^^/g; s/v+/vv/g"
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
4e	vv3
4c	vv1
4G	vv5
4c	^^1
=	=
*-	*-
</script>


### Suppress rendering of melodic contours ###

If the `**deg` tokens contain melodic contour information, then you
can use the `*Xdir` tandem interpretation to hide this information
from the rendered score:

{% include verovio.html
	source="suppress"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="suppress">
**kern	**deg
*clefG2	*Xdir
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1'
4d	^2'
4e	^3'
4f	^4'
4g	^5,,
4e	vv3,,
4c	vv1,,
4G	vv5''
4c	^^1
=	=
*-	*-
</script>

The `*dir` tandem interpretation can be used to start showing the melodic contour
information again.

An alternate method of hiding particular contours, add a `y` after the contour
signifer:

{% include verovio.html
	source="ysuppress"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="ysuppress">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1'y
4d	^y2'y
4e	^y3'y
4f	^y4'y
4g	^5,,
4e	vvy3,,y
4c	vvy1,,y
4G	vv5''
4c	^^y1
=	=
*-	*-
</script>

(Highlighting melodic peaks and troughs.)

Here is an example using the shed filter to remove display of all contours:


{% include verovio.html
	source="shedsup"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="shedsup">
!!!filter: shed -x deg -e "s/[,'v^]//g"
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1'
4d	^2'
4e	^3'
4f	^4'
4g	^5,,
4e	vv3,,
4c	vv1,,
4G	vv5''
4c	^^1
=	=
*-	*-
</script>



### Repeated notes ###

Implement and describe repeated notes, probably using `"` for melodic
approaches to indicate that the scale degree is approached by a
perfect unison.  There is a visual problem with the leap up departure,
which are two single quotes  (`''`).  Also `_` could be used to
indicate that the current note is tied to the previous note.



### Melodic contours across rests ###

It would be useful sometimes to record the contour to a previous/next note
that is on the other side of a rest.  There would need to be a threshold
for the size of the rest which can be crossed in order to trigger a melodic
contour direction (typically allow a contour to be encoded when the rest
is shorter than a beat).



