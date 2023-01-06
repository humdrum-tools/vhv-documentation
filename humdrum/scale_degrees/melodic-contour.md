
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
the signifier `^` is used for both leaps and steps, as well as 
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


### Contours across rests ###

The Humdrum Toolkit command `deg` will not cross over rests to calculate
melodic approaches; however, for a proposed extension to `deg` analysis,
here is a representation system for rests breaking up melodic contours (both
approaching and departing).

A tandem interpretation can be given in a scale degree spine that describes
the duration of rest that can be ignored when calculating melodic contour intervals.
For example, the interpretation `*irest<4` means that any rests less than a quarter before
the scale degree note can be ignored when calculating contours:

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
*	*arest<4
4c	1
8r	r
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



### Hide melodic contours ###

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
signifier:

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

### Contours across slur/phrase boundaries ###

In a future extension to the `deg` command, phrases (`{}`), slurs (`()`, and/or fermatas (;)
can be encoded in `**deg` data in order to disallow labeling melodic contours to
cross them.

{% include verovio.html
	source="phrase"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="phrase">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
{4c	{1'
4d	^2'
4e	^3'
4f	^4'
=2	=2
4g	^5,,
4e	vv3,,
2c}	vv1}
=3	=3
{4cc	{1,
4b	v7,
4a	v6,
4g	v5,,
=4	=4
4e	vv3''
4g	^^5,
2f}	v4}
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

Melodic contours are usually short-circuited by rests that come between
the note of the scale degree and a potential approach or departure pitch.
A proposed extension to the `**deg` representation is to categories these
rests into two basic categories of short rests that are allowed to be
ignored and long rests that cannot be crossed when calculating 
melodic contour approaches and departures.

The information about the rest can be embedded in the scale degree tokens (`p` means "pause"):

| signifier | meaning |
| `p`       | The approach contour crosses a short rest  |
| `pp`      | The approach contour crosses a long rest   |
| `P`       | The departure contour crosses a short rest |
| `PP`      | The departure contour crosses a long rest  |


{% include verovio.html
	source="pcontour"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="pcontour">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*irest<4
4c	1'
4d	^2PP'
4r	r
4f	pp^^4'
4g	^5'
8a	^6P'
8r	r
8b	p^7P'
8r	r
4cc	p^1
=	=
*-	*-
</script>

The `p` or `P` qualifiers should come before the melodic contour information.

This information is not rendered in music notation (at least currently), but
the <a href="/filter/shed">shed</a> filter can be used to remove melodic contours.
Here is an example of removing melodic contours when they cross a large rest:

{% include verovio.html
	source="removep"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="removep">
!!!filter: shed -x deg -e "s/pp(\^\^?|vv?)|PP(''?|,,?)//g"
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*irest<4
4c	1'
4d	^2PP'
4r	rR0
4f	pp^^4'
4g	^5'
8a	^6P'
8r	rr
8b	p^7P'
8r	rr
4cc	p^1
=	=
*-	*-
</script>

Here is an example of suppressing melodic contours across any rest type:

{% include verovio.html
	source="removeall"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="removeall">
!!!filter: shed -x deg -e "s/p+(\^\^?|vv?)|P+(''?|,,?)//g"
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
*	*irest<4
4c	1'
4d	^2PP'
4r	rR0
4f	pp^^4'
4g	^5'
8a	^6P'
8r	rr0
8b	p^7P'
8r	rr0
4cc	p^1
=	=
*-	*-
</script>





