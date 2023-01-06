
## Hide scale degrees ##

If scale degrees need to be hidden for some reason in the music notation, there are two
possible methods of hiding them: (1) append `yy` to the token to hide it, or (2)
use the `*hide` interpretation to hide all following scale degrees (`*Xhide` to
start showing them again).

Here is an example of hiding individual tokens:

{% include verovio.html
	source="hidelocal"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="hidelocal">
**kern	**deg
*clefG2	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2yy
4e	3
4f	4yy
4g	5
4a	6yy
4b	7yy
4cc	1
=	=
*-	*-
</script>

Here is an example of using `*hide`, in this case to hide
scale degrees that don't have any useful function in the key:

{% include verovio.html
	source="hideglobal"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="hideglobal">
**kern	**deg
*clefG2	*
*k[]	*
*C:	*C:
4c	1
4d	2
4e	3
*	*hide
4f#	4+
4g#	5+
4a#	6+
*	*Xhide
4b	7
4cc	1
=	=
*-	*-
</script>

Scale degrees that have an alteration could also be hidden automatically with the <a href="/filter/shed">shed</a> filter:

{% include verovio.html
	source="autohide"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="autohide">
!!!filter: shed -x deg -e "s/([+-]+)/$1yy/g
**kern	**deg
*clefG2	*
*k[]	*
*C:	*C:
4c	1
4d	2
4e	3
4f#	4+
4g#	5+
4a#	6+
4b	7
4cc	1
=	=
*-	*-
</script>




Possible uses of this feature is to encode scale degrees in separate columns for different keys,
and show only the degrees in the active key, possibly showing both scale degrees during a 
modulation between the keys:

{% include verovio.html
	source="modulation"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="modulation">
**kern	**deg	**deg
*clefG2	*	*
*k[]	*	*
*C:	*C:	*G:
*	*	*hide
4c	1	4
4d	2	5
4e	3	6
*	*hide	*Xhide
4f#	4+	7
4g	5	1
4d	6	5
*	*Xhide	*
4B	7	3
4c	1	4
*	*	*hide
4B	7	3
2c	1	4
=	=	=
*-	*-	*-
</script>

In the future key labels will be shown in the notation, making it easier to read.
The top row is for scale degrees in C major while the second row is for G major.

Here is an example of using the <a href="/filter/shed">shed</a> filter to hide
degrees automatically in multiple spines if the are altered:


{% include verovio.html
	source="modulationauto"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="modulationauto">
!!!filter: shed -x deg -e "s/([+-]+)/$1yy/g
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*	*	*
*k[]	*	*	*	*
*C:	*C:	*G:	*F:	*D:
4c	1	4	5	7-
4d	2	5	6	1
4e	3	6	7	2
4f#	4+	7	1+	3
4g	5	1	2	4
4d	2	5	6	1
4B	7	3	4+	6
4c	1	4	4	7-
4B	7	3	4+	6
2c	1	4	4	7-
=	=	=	=	=
*-	*-	*-	*-	*-
</script>




