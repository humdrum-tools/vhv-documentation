## Articulations and ornaments ##

Here is a sampler of note articulations:

{% include verovio.html
	humdrum-min-height="250px"
	source="artic1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic1">
**kern
4ff'
4ff^
4ff`
4ff~
4ff'~
4ff'^
4ff^^
4ff;
=
*-
</script>

Articulations can be place on the opposite side of their automatic location
by adding RDF entries to force the articulation above or below the notehead:

{% include verovio.html
	humdrum-min-height="275px"
	source="artic2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="artic2">
**kern
4f'>
4ff^<
4f`>
4ff~<
4f'~>
4ff'^<
4f^^>
4ff;<
=
*-
!!!RDF**kern: < = below
!!!RDF**kern: > = above
</script>


Here is a sampler of ornaments.  Upper-case ornaments indicate
whole-tone auxiliary notes, and lower-case ornaments indicate
semi-tone auxiliary notes.  If the auxiliary notes require accidentals
in the graphical music notation, then will be added automatically, as
well as cautionary accidentals that may be needed on primary notes
which follow the auxiliary notes of the ornaments.

{% include verovio.html
	humdrum-min-height="250px"
	source="orn1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="orn1">
**kern
*M4/4
=1
2ct
2dT
=2
2fW
2gw
=
2fm
2gM
==
*-
</script>
