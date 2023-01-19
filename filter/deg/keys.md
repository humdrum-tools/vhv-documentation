

## Key interpretations ##


### Modal keys ###

Modal keys can be used to analyze scale degrees:

| Key interpretation | Meaning | Example pitch-classes | 
| --- | --- | --- |
| `*d:dor` | D dorian | DEFGABCD |
| `*e:phr` | E phrygian | EFGABCDE |
| `*F:lyd` | F lydian | FGABCDEF |
| `*G:mix` | G mixolydian | GABCDEFG |
| `*a:aeo` | A aeolean | ABCDEFGA |
| `*b:loc` | B locrian | BCDEFGAB |
| `*C:ion` | C ionian| CDEFGABC |



{% include verovio.html
	source="modes"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="modes">
!!!filter: deg
**kern
*clefG2
*M8/4
*C:
=1
!LO:TX:a:t=major:color=silver
4c
4d
4e
4f
4g
4a
4b
4cc
=
*c:
!LO:TX:a:t=minor:color=silver
4c
4d
4e-
4f
4g
4a-
4b-
4cc
=
*c:dor
!LO:TX:a:t=dorian:color=silver
4c
4d
4e-
4f
4g
4a
4b-
4cc
=
*c:phr
!LO:TX:a:t=phrygian:color=silver
4c
4d-
4e-
4f
4g
4a-
4b-
4cc
=
*C:lyd
!LO:TX:a:t=lydian:color=silver
4c
4d
4e
4f#
4g
4a
4b
4cc
=
*C:mix
!LO:TX:a:t=mixolydian:color=silver
4c
4d
4e
4f
4g
4a
4b-
4cc
=
*c:aeo
!LO:TX:a:t=aeolean:color=silver
4c
4d
4e-
4f
4g
4a-
4b-
4cc
=
*c:loc
!LO:TX:a:t=locrian:color=silver
4c
4d-
4e-
4f
4g-
4a-
4b-
4cc
=
*c:ion
!LO:TX:a:t=ionian:color=silver
4c
4d
4e
4f
4g
4a
4b
4cc
==
*-
</script>


### Modulations ###

When the key changes within a score, the scale degrees will be
relative to the new key:

{% include verovio.html
	source="modulation"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="modulation">
!!!filter: deg
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
=||
*k[f#]
*G:
4g
4a
4b
4cc
4dd
4ee
4ff#
4gg
=
*-
</script>


[ add an option to ignore modulations, maybe `--ignore-modulations` ]


### Setting a default key ###

[To do: do not analyze scale degrees when there is no active key.  This
could be explicitly given with some new interpretation such as `*nokey` and
`*Xnokey`.]

If the input musical score does not have key designations such as `*E:` for
E major, then the `--default-key` option can be used to set the key in which
the scale degrees should be calculated.

{% include verovio.html
	source="makee"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="makee">
!!!filter: deg --default-key E
**kern
4e
4f#
4g#
4a
4b
4cc#
4dd#
4ee
=
*-
</script>


### Forcing analysis in a particular key ###

Similar to setting a default key, you can use the `--force-key` option
to override any key designations in the input data.  Modulations to other
keys besides the initial key will also be overridden.

{% include verovio.html
	source="forcekey"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="forcekey">
!!!filter: deg --force-key d
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
=||
*k[f#]
*G:
4g
4a
4b
4cc
4dd
4ee
4ff#
4gg
=
*-
</script>



