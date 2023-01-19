

## Styling options ##

There are several options that can be used to add styling
for scale degrees in the music notation:


### Circles ###

The `--circle` option will place circles around 
scale degrees.  This is often used on scale degrees
in the bass line in music analysis.

{% include verovio.html
	source="circle"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="circle">
!!!filter: deg --circle
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>

If you want to only circle a selection of scale degrees, you can
use `*Xcircle` to stop circling scale degrees. This must be done
after running the `deg` filter, because the styling options are
applied once to the entire score.  Here is an example of manually
highlighting the tonic triad scale degrees:


{% include verovio.html
	source="toniccircle"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="toniccircle">
!!!Xfilter: deg --circle
**kern	**deg
*k[]	*
*C:	*C:
*	*circ
4c	1
*	*Xcirc
4d	2
*	*circ
4e	3
*	*Xcirc
4f	4
*	*circ
4g	5
*	*Xcirc
4a	6
4b	7
*	*circ
4cc	1
*	*Xcirc
=	=
*-	*-
</script>

You can, however, give different styling to different `**deg` analysis
spines by running the `deg` filter more than once on the score while
using the `-s` or `-k` options to select `**kern` spines to analyze

Below is an example of circling the degrees on one staff, but not
ones on the other staff:

```bash
deg -k1 --circle | deg -k2
```

{% include verovio.html
	source="circandnocirc"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="circandnocirc">
**kern	**deg	**kern	**deg
*k[]	*	*k[]	*
*C:	*C:	*C:	*C:
*	*circ	*	*
4c	1	4c	1
4B	7	4d	2
4A	6	4e	3
4G	5	4f	4
4F	4	4g	5
4E	3	4a	6
4D	2	4b	7
4C	1	4cc	1
=	=	=	=
*-	*-	*-	*-
</script>

The `-s` option can be used, but is less useful since the spine may numbers
change after each pass through the `deg` filter.  These two filter commands
will produce the same example output give above:

```bash
deg -s1 --circle | deg -s3
```

For this case, the `-s 3` option analyzes the second `**kern` spine, which
changes to the third spine after the first pass through the `deg` filter.

```bash
deg -s2 | deg -s1 --circle
```

For this case, the first `**kern` spine remains at the beginning of the
line since the `**deg` spine added in the first pass becomes the third
spine in the data.



### Hats ###

The `--hat` option will place carets (circumflexes) over scale
degrees in the graphical music notation.  These are typically
added to the melody line in music analysis.

{% include verovio.html
	source="hat"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="hat">
!!!filter: deg --hat
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>

Here is an example of circling the scale degrees in the bottom 
part and then hatting the degrees in the top part:

```bash
deg -s2 --hat | deg -s1 --circle
```

{% include verovio.html
	source="circhat"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="circhat">
!!!Xfilter: deg -s2 --hat | deg -s1 --circle
**kern	**deg	**kern	**deg
*k[]	*	*k[]	*
*C:	*C:	*C:	*C:
*	*circ	*	*
*	*	*	*hat
4c	1	4c	1
4B	7	4d	2
4A	6	4e	3
4G	5	4f	4
4F	4	4g	5
4E	3	4a	6
4D	2	4b	7
4C	1	4cc	1
=	=	=	=
*-	*-	*-	*-
</script>



### Boxes ###

The `--box` option will place a box around in each scale degree.

{% include verovio.html
	source="box"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="box">
!!!filter: deg --box
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>



### Color ###

The `--color` option can be used to set the color of the
scale degrees when displaying with music notation.


{% include verovio.html
	source="mycolor"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="mycolor">
!!!filter: deg --color crimson
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>

`**deg` spines can be given different colors by selectively 
running the deg filter, applying one color for each pass through
the `deg` filter:

```bash
deg -k1 --color crimson | deg -k2 --color dodgerblue
```

{% include verovio.html
	source="mycolor2"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="mycolor2">
!!!Xfilter: deg -k1 --color crimson | deg -k2 --color dodgerblue
**kern	**deg	**kern	**deg
*k[]	*	*k[]	*
*C:	*C:	*C:	*C:
*	*color:crimson	*	*color:dodgerblue
4c	1	4c	1
4B	7	4d	2
4A	6	4e	3
4G	5	4f	4
4F	4	4g	5
4E	3	4a	6
4D	2	4b	7
4C	1	4cc	1
=	=	=	=
*-	*-	*-	*-
</script>



### Place degrees above the staff  ###

By default scale degrees will be displayed below the staff
when shown in a musical score.  You can ass the `--above` option
to show them above the staff.

{% include verovio.html
	source="above"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="above">
!!!filter: deg --above
**kern
*k[]
*C:
4c
4d
4e
4f
4g
4a
4b
4cc
=
*-
</script>

Here is an example of circling the bottom staff scale degrees, then
hatting the degrees on the top staff and placing them above the staff:

```bash
deg -k1 --circle | deg -k2 --hat --above
```

{% include verovio.html
	source="circhatabove"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="circhatabove">
!!!Xfilter: deg -k1 --circle | deg -k2 --hat --above
**kern	**deg	**kern	**deg
*k[]	*	*k[]	*
*C:	*C:	*C:	*C:
*	*	*	*above
*	*circ	*	*
*	*	*	*hat
4c	1	4c	1
4B	7	4d	2
4A	6	4e	3
4G	5	4f	4
4F	4	4g	5
4E	3	4a	6
4D	2	4b	7
4C	1	4cc	1
=	=	=	=
*-	*-	*-	*-
</script>


If you want to display both scale degree analyses below the bottom 
staff, you can use the [extract](/filter/extract) filter to rearrange
the `**deg` spines:

```bash
deg -k1 --circle | deg -k2 --hat | extract -s 1,4,2,3
```

{% include verovio.html
	source="bothbelow"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="bothbelow">
!!!Xfilter: deg -k1 --circle | deg -k2 --hat | extract -s 1,4,2,3
**kern	**deg	**deg	**kern
*k[]	*	*	*k[]
*C:	*C:	*C:	*C:
*	*	*circ	*
*	*hat	*	*
4c	1	1	4c
4B	2	7	4d
4A	3	6	4e
4G	4	5	4f
4F	5	4	4g
4E	6	3	4a
4D	7	2	4b
4C	1	1	4cc
=	=	=	=
*-	*-	*-	*-
</script>

Notice that the order of the `**deg` spines are from highest staff
to lowest staff when they are placed below the staff.  If you want
to show both `**deg` spines above the staff, then the order of the
`**deg` spines has to be reversed:

```bash
deg -k1 --circle | deg -k2 --hat | extract -s 1,2,4,3
```

{% include verovio.html
	source="bothbelow"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="bothbelow">
!!!Xfilter: deg -k1 --circle | deg -k2 --hat | extract -s 1,3,4,2
**kern	**kern	**deg	**deg
*k[]	*k[]	*	*
*C:	*C:	*C:	*C:
*	*	*circ	*
*	*	*	*hat
4c	4c	1	1
4B	4d	7	2
4A	4e	6	3
4G	4f	5	4
4F	4g	4	5
4E	4a	3	6
4D	4b	2	7
4C	4cc	1	1
=	=	=	=
*-	*-	*-	*-
</script>

To change the side of the staff within the score, you can 
edit the score after passing it through the `deg` filter,
adding `*below` to cancel the `*above` placement:


{% include verovio.html
	source="below"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="below">
!!!Xfilter: deg --above
**kern	**deg
*k[]	*
*C:	*C:
*	*above
4c	1
4d	2
4e	3
4f	4
4g	5
4a	6
*	*below
4b	7
4cc	1
=	=
*-	*-
</script>





