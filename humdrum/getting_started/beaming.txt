## Beaming ##

Beams work in a similar manner to ties.  The `L` character
indicates the start of a beam, and the `J` character indicates
the end of a beam.

{% include verovio.html
	humdrum-min-height="490px"
	evenNoteSpacing="1"
	source="beam1"
	scale="55"
	pageWidth="475"
%}
<script type="application/x-humdrum" id="beam1">
**kern
*M3/4
=1
8c
8d
8e
8f
8g
8a
=2
8cL
8dJ
8eL
8fJ
8gL
8aJ
=3
*M6/8
8cL
8d
8eJ
8fL
8g
8aJ
==
*-
</script>

Try adding beams with irregular groupings in the first measure of the example.

### Lazy beaming ###

VHV uses a lazy beaming system to beam notes together.  Rather than
specifying the beginning/ending of each sub-beam or beamlet direction,
you instead indicate the beginning/ending of a beamed group of
notes with the `L` and `J` characters (*i.e.*, encode only the primary
sub-beam):

Encoding a full description of sub-beams:

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam2"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam2">
**kern
*M2/4
16.eLL
32fk
16.e
32fJJk
8fL
16gL
16aJJ
==
*-
</script>

which is equivalent to this lazy-beam encoding of only the primary beam (the beam
furthest from the noteheads):

{% include verovio.html
	humdrum-min-height="225px"
	evenNoteSpacing="1"
	source="beam3"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam3">
**kern
*M2/4
16.eL
32f
16.e
32fJ
8fL
16g
16aJ
==
*-
</script>

Beams cannot currently be drawn across barlines.  If the beam
beginnings/endings do not balance each other out within a measure, none
of the notes in the measure will be beamed.

{% include verovio.html
	humdrum-min-height="425px"
	evenNoteSpacing="1"
	source="beam4"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam4">
**kern
*M4/4
=1
8cL
8f
8a
8eJ
8fL
8g
8f
8aJ
=2
8cL
8f
8a
8e
8fL
8g
8f
8aJ
==
*-
</script>


### autobeam filtering ###

The [autobeam filter](/filters/autobeam) can be used to beam notes together automatically, 
based on the prevailing time signature:

{% include verovio.html
	humdrum-min-height="365px"
	evenNoteSpacing="1"
	source="beam5"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="beam5">
**kern
*M3/4
8c
8d
8e
8f
8g
8a
=
*M6/8
8c
8d
8e
8f
8g
8a
==
*-
!!!filter: autobeam
</script>
