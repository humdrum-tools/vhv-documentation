
## Solf&egrave;ge ##

The `--solfege` option (short version `--solf`) can be used
to display scale degrees as solf&egrave;ge syllables rather
than as numbers.


{% include verovio.html
	source="solf"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="solf">
!!!filter: deg --solfege
**kern
*k[]
*B:
4B
4c#
4d#
4e
4f#
4g#
4a#
4b
=
*-
</script>


By default the solf&egrave;ge syllables are relative to the key, so 1=do, 2=re, etc.  If you want 
fixed solf&egrave;ge syllables (C=do, D=re, etc.), then use the `--force-key C` option:


{% include verovio.html
	source="solffix"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="solffix">
!!!filter: deg --solfege --force-key C
**kern
*k[]
*B:
4B
4c#
4d#
4e
4f#
4g#
4a#
4b
=
*-
</script>

Solf&egrave;ge syllables are chromatic, where sharped pitch classes
typically change the vowel to `i`, and flatted change the vowel to
`e` (or `a` if the default syllable uses `e`, such as `di` for the
raised tonic, or C&#x266f; in fixed do.  Only "black keys" have a
chromatic syllable name; otherwise, the syllable will be enharmonically
changed to the next scale degrees syllable.  For example the flatted
tonic, or C&#x266d; in fixed do, will be displayed as `ti` rather than
`de`.

If you do not want chromatic alterations included in the solf&egrave;ge
syllables, remove them with the [shed](/filter/shed) before displaying
in music notation:

```bash
deg --solfege --force-key C | shed -x deg -e "s/[+-]+//g"
```

{% include verovio.html
	source="solfdia"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="solfdia">
!!!filter: deg --solfege --force-key C | shed -x deg -e "s/[+-]+//g"
**kern
*k[]
*B:
4B
4c#
4d#
4e
4f#
4g#
4a#
4b
=
*-
</script>


[Maybe add an option such as `**solfF` to display `do` as `ut` and `ti` as `si`, and `so` as `sol`.]


