
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
*clefG2	*arr	*v:**deg:
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
*clefG2	*arr
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



