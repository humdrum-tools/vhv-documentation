

## Chromatic alterations ##

Chromatic alterations are displayed as accidentals before
the scale degrees by default.  These accidentals are relative
to the analysis key.  For example in C minor, `7+` is the 
raised 7th scale degree, which would be B natural, since the
nominal pitch in C (natural) minor is a B-flat.  In music 
notation this will be shown as "&#x266d;7".

{% include verovio.html
	source="melodicminor"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="melodicminor">
!!!filter: deg
**kern
*k[]
*a:
4A
4B
4c
4d
4e
4f#
4g#
=
4a
4gnX
4fnX
4e
4d
4c
4B
4A
=
*-
</script>

[To do: place the accidental in front of the scale degree and add an
option `*accrev` to allow it displayed after the degree.]


You can add the `--arrow` option to display chromatic
alterations as up/down arrows after the scale degree
in music notation.

{% include verovio.html
	source="melodicminorarrow"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="melodicminorarrow">
!!!filter: deg --arrow
**kern
*k[]
*a:
4A
4B
4c
4d
4e
4f#
4g#
=
4a
4gnX
4fnX
4e
4d
4c
4B
4A
=
*-
</script>

[To do: add an interpretation `*arrrev` to place the arrows in front 
of the scale degree.]
