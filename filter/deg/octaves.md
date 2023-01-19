

## Octaves ##

Octave information about the pitches can be preserved in the
scale degree analysis by adding the `--octave` option.  The output
data will be placed into a `**degree` spine, similar to the output
of the `degree` tool in the Humdrum Toolkit.  These octaves will be
displayed as subscript numbers after the scale degree when displayed
in music notation.

{% include verovio.html
	source="oct"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="oct">
!!!filter: deg --octave
**kern
*k[b-]
*F:
4F
4A
4c
4f
4a
4cc
4ff
=
*-
</script>

Note that the middle-C octave is labeled as the 4th octave.



