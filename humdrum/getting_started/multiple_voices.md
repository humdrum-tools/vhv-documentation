## Multiple voices on a staff ##

Spine split manipulators (`*^`) and spine merge manipulators (`*v`) are used
to add or remove voices/layers on a staff.  Note that the highest part 
on the staff will typically be left most (opposite of the staff ordering 
from lowest to highest).

{% include verovio.html
	humdrum-min-height="210px"
	source="multi1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi1">
**kern
*M4/4
*^
2..gg	4b
.	4a
.	4g
.	4f
8ff	.
*v	*v
=
*-
</script>

Notes sounding together in the different voices are placed on the same line, and
if the other voice is sustaining, a `.` character is used as a place holder for
that voice (the dot is called a *null token* in Humdrum terminology).

### Partial voices/layers ###

Voices/layers which do not continue throughout the measure can be encoded
in two equivalent manners: (1) splitting and merging the spine as needed in 
the measure, or (2) adding invisible rests to fill in the voice/layer for the
entire measure.  For method #1, note that the spine merging cannot occur until 
the end of both sounding notes in each layer.

{% include verovio.html
	humdrum-min-height="360px"
	source="multi2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="multi2">
**kern
*M4/4
=1
*^
2cc	4a
.	4g
*v	*v
4f
4e
=2
*^
2cc	4a
.	4g
2ryy	4f
.	4e
*v	*v
=
*-
</script>
